Changes since 0.6.0 onwards.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.0.1 (2021-11-21)
~~~~~~~~~~~~~~~~~~~
* Attempted fix in 0.9.18 to avoid hidden files in dataset() failed - fixed.

1.0.0 (2021-11-17)
~~~~~~~~~~~~~~~~~~~
* Updated readme, notebooks and cookbook for release of version 1.0.0
 
0.9.18 (2021-11-16)
~~~~~~~~~~~~~~~~~~~
* Include "CH" at the start of pattern matches for file names in dataset.py to
  avoid finding hidden files. 

0.9.17 (2021-11-13)
~~~~~~~~~~~~~~~~~~~
* Update StarProperties and core for new location and format of SWEET-Cat
* Added backend option to MultiVisit and Dataset fit routines (#169)
* Added rho, sigma and tau to SHOTerm output (#206)

0.9.16 (2021-10-27)
~~~~~~~~~~~~~~~~~~~
* Remove html versions of example notebooks
* Added parameter hint for ramp in models.FactorModel
* Use np.nanmean() and np.nanmedian() in utils.lcbin
* Bug fix for unwrap=True in multivisit - dfdsin2pi, dfdcos2phi, dfdsin3phi
  and dfdcos3phi terms were not be removed.

0.9.15 (2021-10-20)
~~~~~~~~~~~~~~~~~~~
* Fixed plotting bug for models not in phase order in MultiVisit.plot_fit()
* Dataset.cds_data_export: acknowledgments -> acknowledgements

0.9.14 (2021-10-19)
~~~~~~~~~~~~~~~~~~~
* Added dependency_links for python-dace-client to setup.py
* Updated INSTALLATION 
* Replaced try/except/pass guards around dace imports in all files with
  redirect_syserr(devnull). 
* Updated examples/Notebooks

0.9.13 (2021-10-17)
~~~~~~~~~~~~~~~~~~~
* Major re-factoring of multivisit needed to fix/clarify what is meant by
  detrended flux for plotting and table output routines. 
* Added calculate_coefficients.py script
* Added white-noise baseline to dataset.plot_fft()
* Exclude nu_max plot for stars Teff<5000K in dataset.plot_fft
* Added median background count rate to summary on ingest in Dataset
* Renamed flatchain attribute in MinimizerResult object returned by fitting
  routines to flat_chain to avoid conflict with documented behaviour
* Added cds_data_export() function to MultiVisit
* Guard against failed dace import in planetproperties (#232)
* Fix bug in combine that was excluding valid range of sigma_ext values, not
  including it. 

0.9.12 (2021-08-04)
~~~~~~~~~~~~~~~~~~~
* Avoid warnings due to truncated strings for RA/Dec in make_xml_files
* Changed default suffix in make_xml_files to that required for CHEOPSim
* Added --checker and --directory options to make_xml_files
* Convert K_val and K_err to m/s in planetproperties (#228)
* Fixed planetproperties bug for 'NaN' values in dace obj_rv_k_mps data
* Fix problem with ambiguous planet identifiers in TEPCat for planetproperties
* Changed keywoards D->depth and W->width for planetproperties to avoid
  confusion with D and W in transit model
  
0.9.11 (2021-04-24)
~~~~~~~~~~~~~~~~~~~
* Added data.cds_data_export()
* Add result.lnlike to output of dataset and multivisit fitting routines.
* Add log_sigma keyword to dataset.lmfit_transit and dataset.lmfit_eclipse
* Correct calculation of result.chisqr in dataset.lmfit_transit and
  dataset.lmfit_eclipse
* Catch invalid combinations of b and k in dataset._log_prior() and remove
  restriction b < 1+k.
* Catch non-finite derived parameters in multivisit._log_posterior
* Correct typo in combine.py
* Added dfdsmear to _make_labels in dataset (#224)
* dataset.lc['bg'] is now normalized by the median flux in the aperture
* Added explanation of what is meant by detrended flux to multivisit docstring
  
0.9.10 (2021-03-23)
~~~~~~~~~~~~~~~~~~~
* Update dataset.py for compatibility with DACE API 2.0.0
* Improve output from utils.parprint for very large/small values
* Changed definition of delta-x and delta-y used in decorrelation so that
  dfdx and dfdy are more closely related to magnitude of the instrumental
  noise in the light curve correlated with x and y (~factor 2 change).
* Changed default upper limit on b in Multivisit from 1 to 1.5
* Use Gaia G magnitude in XML files from make_xml_files

0.9.9 (2021-02-04)
~~~~~~~~~~~~~~~~~~
* BUG FIX - unwrap option was not working correctly in MultiVisit - only
  dfdcosphi and dfdsinphi terms were used 
* BUG FIX - MultiVisit residuals arrays were calculated and plotted 
  incorrectly
* Added return_values option to Dataset.transit_noise_plot() (#197)
* Enable fitting of datasets from older version missing deltaT in Dataset
* Fix bug in MultiVisit where mixture of datasets with/without glint functions
  would not load (#164)
* Fix bug in reporting smear correction for Dataset.get_lightcurve()
* Added iteration limit to initialisation of walkers in MultiVisit
* Changed default upper limit on W to 0.2 in MultiVisit
* Exclude negative eclipse depths for MultiVisit.fit_eclipse with etv=True
* Improved initialisation of individual eclipse depths for
  MultiVisit.fit_eclipse with etv=True  
* Added html version of WASP-189 and KELT-11b notebooks to examples/Notebooks

0.9.8 (2021-01-20)
~~~~~~~~~~~~~~~~~~
* Get metadata from SCI_RAW_SubArray instead of SCI_RAW_HkCe-SubArray
* Exclude negative fluxes when loading light curve in Dataset

0.9.7 (2020-12-24)
~~~~~~~~~~~~~~~~~~
* Added metadata to dataset (#93)
* Added correct_ramp to dataset
* Added ramp parameter to dataset.fit_transit and fit_eclipse.
* Added ramp to MultiVisit
* AIC and BIC now correct and consistent for all fitting methods (#177)
* Improve selction of min/max values for parameters in MultiVisit
* Changes for DRP13 compatibility.
* Reduced the number Notebooks in examples/Notebooks
* Added WASP-189.ipynb to examples/Notebooks 
* Added predicted amplitude of ramp to output of dataset.get_lightcurve
* Added data_ylim and res_ylim keywords to MultiVisit.plot_fit().
* Improved calculation of y-axis limits for MultiVisit.plot_fit() if
  res_offset=0
* Added observing efficiency, etc. to dataset.get_lightcurve verbose output.
* Added return_samples option to MultiVisit.massradius()
* Added input quantities to output of funcs.massradius()

0.9.6 (2020-11-24)
~~~~~~~~~~~~~~~~~~
* Force user to set decontaminate option in dataset.get_lightcurve()
* Add "thin" keyword option to MultiVisit fit routines.
* Added return_nan_on_error to tzero2tperi and used it in funcs/models
* Added acceptance_fraction to MultiVisit output result
* Updated diagnostic plots to show contamination and smear
* Updated examples/Notebooks/KELT11b-tutorial.ipynb
* Flux normalisation now done after high point rejection. (#166)
* Added glint_scale to Bayes Factors section of lmfit report (#162)
* Added installation help for celerite2 in README (#170)
* Added WASP-189 to examples/Notebooks


0.9.5 - skipped
~~~~~~~~~~~~~~~

0.9.4 
~~~~~~~~~~~~~~~~~~
* Changed calculation of _log_prior in dataset to allow fitting of grazing
  transits with 1 < b < 1+k
* Changed the way min/max values of parameters are handled in MultiVisit to
  enable user-defined values to be set via keyword arguments.  
* Correct docstring for h1h2_to_q1q2
* dataset.get_lightcurve, require user to specify decontaminate True or False
* Added dataset.smear attribute and dfdsmear

0.9.3 (2020-10-10)
~~~~~~~~~~~~~~~~~~
* Fixed missing Bayes factor for d2fdt2 (#159)
* Changed aperture used to extract metadata to DEFAULT in dataset

0.9.2 (2020-09-25)
~~~~~~~~~~~~~~~~~~
* Removes autograd from requirements in setup.py
* Added solar options to funcs.massradius()
* Changed default thin=4 to thin=1 in dataset.emcee_sampler()
* Fixed bug in MultiVisit for default log_Q value (#155)
* Added PlanetProperties
* Updated KELT-11b-tutorial.ipynb to show use of PlanetProperties
* Update example TESS notebooks to celerite2

0.9.1 (2020-09-10)
~~~~~~~~~~~~~~~~~~
* celerite -> celerite2
* Fix missing DRP report due to new file structure for simulation data (#146)

0.9.0 (2020-09-09)
~~~~~~~~~~~~~~~~~~
* Added tqdm to requirements in setup.py
* Added "unwrap" option to MultiVisit fit routines fit_transit(), etc. 
* Set mean value of glint function to 0 in dataset.add_glint().
* Fixed bug with evaluation of glint function in MultiVisit 
* Fixed bug in MultiVisit.plot_fit() - model plotted using old parameters

0.8.5 (2020-09-02)
~~~~~~~~~~~~~~~~~~
* Added funcs.tperi2tzero() and funcs.eclipse_phase()
* Added "Bayes factors" section to dataset.lmfit_report()
* Added MultiVisit.fit_eblm
* Added pycheops/examples/Notebooks/KELT-11b-tutorial.ipynb

0.8.4 (2020-08-30)
~~~~~~~~~~~~~~~~~~
* Fix parameter hint prefix problem in models (#141)
* Fix -ve offset ylimit problem in MultiVisit (#139)
* Added warning is failed to update TEPCat in funcs.massradius (#137)
* Fix bug in dataset and MultiVisit if only 1 variable in trailplot (#130)
  
0.8.3 (2020-07-30)
~~~~~~~~~~~~~~~~~~
* Fix astype(int) problem in __init__.py for windows users
* Fix bug in MultiVisit where priors on derived parameter were ignored.
  
0.8.2 (2020-07-26)
~~~~~~~~~~~~~~~~~~
* Read datasets into MultiVisit object in a logical order (#133)
* Update T0 in dataset.emcee.params_best and dataset.emcee.chain in MultiVisit
* Fix copy.copy bug in dataset.should_I_decorr() 

0.8.1 (2020-06-29)
~~~~~~~~~~~~~~~~~~
* Added MultiVisit.ttv_plot()
* Changed parameter names to ttv_01, L_01, etc. in MultiVisit to cope with
  MultiVisit objects with >9 datasets.
* Added min/max values from params to modpars in MultiVisit
* MultiVisit datadir join bug fix
* Fixed title keyword option in MultiVisit.plot_fit()

0.8.0 (2020-06-28)
~~~~~~~~~~~~~~~~~~
* Added MultiVisit class
* Added load() and save() to dataset
* Added dace keywords to StarProperties
* Added option to set user-defined values using a 2-tuple in StarProperties 
* Bug fixes for animate_frames 
* Add requirement for matplotlib 3.2.2 to setup.py
* Get fits extensions by name in dataset
* Updated notebooks in examples/Notebooks

0.7.8 (2020-06-03)
~~~~~~~~~~~~~~~~~~
* Suppress warnings from matplotlib.animate in dataset
* Subarray metadata search fix (#110)
* Add check for finite flux values in dataset.get_lightcurve()
* should_I_decorr bug fix, code cleanup and expansion (#115)
  
0.7.7 (2020-05-12)
~~~~~~~~~~~~~~~~~~
*N.B.* New behaviour for dataset.get_lightcurve()

* dataset.get_lightcurve() now subtracts contaminating flux by default
* added decontaminate keyword to dataset.get_lightcurve() (#82)
* dataset.add_glint() function is now  periodic (#87)
* Added outlier rejection to dataset.diagnostic_plot (#84)
* Add functions to dataset to view/animate images (#83)
* Updated comments re: decorrelation in example notebooks 
* Bug fix to moon angle calculation in dataset.py
* Fix math errors in funcs.massradius caused by negative values (#104)
* Fix math errors in dataset.massradius caused by negative values (#104)
* dataset.get_subarray adapted to allow use of simulated data

0.7.6 (2020-05-01)
~~~~~~~~~~~~~~~~~~
* Fixed y-axis title bug in dataset.rollangle_plot (#85).
* Added robust grid search to funcs.tzero2tperi

0.7.5 (2020-04-27)
~~~~~~~~~~~~~~~~~~
* Bug fix in dataset for d2fdx2, d2fdy2, d2fdt2
* Reduced size of initial bracketing interval in funcs.tzero2tperi
* Wrong units on stellar mass/radius in funcs.massradius fixed
* Fixed decorr with bg, contam, sin3phi, cos3phi bug (#80)
* Added fallback in utils/parprint() if error is 0

0.7.4 (2020-04-23)
~~~~~~~~~~~~~~~~~~
* Added dataset.planet_check
* Added moon option to add_glint
* Dropped angle0 option from dataset.rollangle_plot
* Bug fix in funcs.massradius for calls without m_star or r_star

0.7.3 (2020-04-22)
~~~~~~~~~~~~~~~~~~
* Documentation update for funcs.massradius
* Bug fix in decorr and should_I_decorr (#73)

0.7.2 (21-04-2021)
~~~~~~~~~~~~~~~~~~
* Improved edge behaviour of dataset.clip_outliers
* Added option in starproperties to not raise error if star not in SWEET-Cat
* Added plot_model to dataset.plot_lmfit
* Fixed offset problem for transit model in dataset.plot_emcee
* Added sini to derived parameters listed in dataset
* Improved funcs.m_comp using closed-form solution of cubic polynomials.
* Added funcs.massradius and dataset.massradius
* Added catch for e>0.999 in models

0.7.1 (14-04-2020)
~~~~~~~~~~~~~~~~~~
* Fixed dataset flux.nanmean issue caused by merge on github.

0.7.0 (13-04-2020)
~~~~~~~~~~~~~~~~~~
* Added kwargs to dataset.corner_plot
* Added binned data points to dataset.plot_lmfit and dataset.plot_emcee
* Added utils.lcbin and utils.parprint
* Moved priors appended to dataset.lmfit.residual to their own object
  dataset.lmfit.prior_residual and added dataset.npriors
* Fixed bug on models.FactorModel for dfdsin3phi and dfdcos3phi
* Tidied-up/improved interpolation of dependent variables in dataset
* Fixed bug with xoff being assigned to yoff in dataset.lmfit_transit() and
  dataset.lmfit_eclipse()
* Added dataset.rollangle_plot()
* Set stderr and correl values for dataset.emcee.params_best - breaks printing
  otherwise.
* Changed logic in dataset.emcee_sampler() so add_shoterm works if param
  keyword is specified.
* Enabled show_priors option in dataset.corner_plot()
* Added kwargs to dataset.lmfit_report() and dataset.emcee_report
* Added RMS residual to dataset.lmfit_report() and dataset.emcee_report()
* Added dataset.mask_data()
* Added dataset.plot_fft()
* Added dataset.trail_plot()
* Updated dataset examples in pycheops/examples/Notebooks
* Removed bug in dataset when setting h_1, h_2 from tuple.
* Removed bug when plotting GPs in dataset that caused an offset ("flux0=flux
  is not a copy" issue).
* Added ld.atlas_h1h2_interpolator and used it in starproperties
* Added ld.phoenix_h1h2_interpolator and used it in starproperties
* Moved pickle files used in ld.py to user's cache directory instead of the
  installation data directory.
* Added dataset.add_glint() and scaled glint correction to lmfit/emcee fits

0.6.9 (2020-04-02)
~~~~~~~~~~~~~~~~~~
* Bug fix for use of bg and contam in dataset.py 
* Changed to interp1d from InterpolatedUnivariateSpline in dataset.py

0.6.8 (2020-04-02)
~~~~~~~~~~~~~~~~~~
* Fixed bug for new users - not possible to run setup_config()
* Fixed bug in instrument.py - log_exposure_time.p not used anymore

0.6.7 (2020-04-02)
~~~~~~~~~~~~~~~~~~
* Set vary=False default for f_c and f_s in TransitModel.
* Replaced vectorize in func/m_comp() with map.
* Fixed bug in dataset.lmfit_transit() and dataset.lmfit_eclipse() for fitting 
  d2fdx2, d2fdy2 and d2fdt2.
* Added dfdcontam to models/FactorModel() 
* Added dfdbg and dfdcontam to dataset.lmfit_transit and dataset.lmfit_eclipse()
* Changed CHANGELOG format
* Improved/simplified dataset.clip_outliers()
* Removed broken pool option from dataset.emcee_sampler()
* Additional parameter checks in EclipseModel and TransitModel
* Change default to reject_highpoints=False in dataset
* Include pycheops version with fit reports in dataset
* Added nu_max to funcs
* Updated instrument.count_rate and instrument.exposure_time to make them
  consistent with spreadsheet ImageETCv1.4, 2020-04-01
* Added instrument.cadence()
* Updated make_xml_files
* Updated pycheops/examples/Notebooks/TestThermalPhaseModel.ipynb 

0.6.6
~~~~~
* Added numba version requirement to setup.py.
* Added V magnitude and spectral type information to dataset object.
* Add light curve stats to dataset objects.
* Added "local" option to dataset.transit_noise_plot.
* Set max value of D to 0.25 in models.TransitModel and models.EBLMModel.
* Fixed bug with missing prefix in expr for param hints in models..
* Added model.PlanetModel.
* Added dataset.lc['bg'].
* Updated conf.py for sphinx documentation.

0.6.5
~~~~~~
* Change BJD_late to 2460000.5 in example make_xml_file input files.
* Add --count_rate option to make_xml_files

0.6.4  (2020-02-19)
~~~~~~~~~~~~~~~~~~~
* Simplified call to astroquery.gaia in make_xml_files - fixes HTTPError 302
  problem that started happening since the last update. Change at the server(?)

0.6.3 (2020-02-01)
~~~~~~~~~~~~~~~~~~
* Completed the changes from version 0.6.2 - store pickle files in user's cache
  directory, interpolation of exposure times, update spectral-type T_eff G-V
  values.
* Fixed J=L/D in EclipseModel
* Added EBLMModel to models.
* Added a few examples of TESS analysis to  examples/Notebooks
* Changed target TESS_fit_EB.ipynb to TESS_fit_EBLM.ipynb  fit to EBLM J0113+31.

0.6.2 (2020-01-25)
~~~~~~~~~~~~~~~~~~
* Store pickle files in user's cache directory to avoid permissions issues
  with root user installations. (not finished)
* Added --scaling-factor-percent option to make_xml_files.
* Fix bug in make_xml_files where T_exp is stored as an integer - now float
* Improved interpolation of exposure times. (not finished)
* Updated spectral-type T_eff G-V values in make_xml_files (not finished)
* Bug fix for cases where log_g, [Fe/H] not defined in sweetcat.
* Add option for user-defined parameters in starproperties.

0.6.1 (2019-11-22)
~~~~~~~~~~~~~~~~~~
* Remove error message if there is no imagette data in the dataset.
* Remove DACE import warning in dataset
* Added calculation of prior on P(D, W, b) for transit/eclipse fitting assuming
  uniform priors on cos(i), log(k) and log(a/R*).  

0.6.0 (2019-11-06)
~~~~~~~~~~~~~~~~~~
* Generate pickle files in data directory at run time when first needed. 
* Single-source version number from pycheops/VERSION
* Removed stagger_claret_interpolator and stagger_mugrid_interpolator from ld.

