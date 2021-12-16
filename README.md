# push_horizon_finder
[![DOI](https://zenodo.org/badge/438798803.svg)](https://zenodo.org/badge/latestdoi/438798803)

Post-process AGILE general relativistic hydrodynamics output from completed PUSH simulations to identify the formation of black hole horizons.

# Installation

## Python
The main package dependencies are described in `environment.yml`. If you want to install this environment with anaconda (named `push_horizon_finder` by default), simply run:
```
conda install --file environment.yml
```
while in the root directory of this repository. If you don't yet have Jupyter lab or notebook installed, you can also do so with anaconda, as detailed here: https://jupyter.org/install. Additionally, Jupyter servers can be run directly in some IDEs like VSCode; in those cases, installation will be handled by the particular IDE's package management system. 

## Mathematica
If you have access to Mathematica through your institution, please refer to their installation instructions; if you're installing independently, follow the instructions given by Wolfram: https://www.wolfram.com/mathematica/.

To use the Mathematica scripts in this repository, you'll also need the GRhelper library. This is a library developed by Chris Evans at UNC Chapel Hill and David Brown at NC State; at the moment, I'm not sure if this can be publicly released, however, you may find success by asking David Brown nicely at jbrown@ncsu.edu.

# Use
The horizon finder is implemented in `push_apparent_horizon_finding-AGILE_expansion.ipynb`, which must be opened with a Jupyter notebook or other software with a Jupyter server backend. The references to `./s15.0_trise400_k4.3` and `./s22.2_trise400_k4.3` refer to completed PUSH simulations that explode and fail to explode, respectively. At this time, we cannot publicly release those data. However, for reference, the code expects that they are structured, at minimum, like:
```
simulation_root_directory (e.g. s15.0_trise400_k4.3)
|_ data
    |_ {series}{eos}{mass}_0001.stp (e.g. s15.0_0001.stp)
    |_ {series}{eos}{mass}_0002.stp
    ...
    |_ {series}{eos}{mass}_{final recorded timestep}.stp
```
with a subfolder named `data`, containing the `.stp` files which record hydrodynamic information from AGILE at each timestep.

The Jupyter notebook should be executed sequentially; for detailed descriptions of what it is calculating and why, see `PUSH_GR-FALL_2021-FINAL_REPORT.pdf` and the markdown cells in the Jupyter notebook. 

# Manifest
- The horizon finder is implemented in `push_apparent_horizon_finding-AGILE_expansion.ipynb` (see Use, above).
- Physical motivation and derviations are provided in `PUSH_GR-FALL_2021-FINAL_REPORT.pdf` (coherently) and `PUSH_GR.pdf` (less coherently). The former document is the final report that Noah Wolfe completed to receieve PY 499 class credit at NC State in the Fall 2021 semester; the latter document is his notes on numerical relativity, AGILE, and horizon finding, some of which ended up in the final report. Readers beware of the latter document.
- The mathematica scripts in `./mathematica` contain calculations and manipulations of general relativity vector and tensor quantities. The utility of their results in deriving results or implementing the horizon finder in code is referenced inline in the relevant documents.
- A possibly incomplete / overcomplete list of references, in bibtex format, can be found in `refs.bib`.

# References
## General Relativity
- Frauendiener, J. Miguel Alcubierre: Introduction to 3 + 1 numerical relativity. Gen Relativ Gravit 43, 2931 (2011). https://doi.org/10.1007/s10714-011-1195-5
- Misner, Charles W., Kip S. Thorne, and John Archibald Wheeler. Gravitation. Macmillan, (1973).
## PUSH and AGILE
- The most modern version of PUSH is described in: Ebinger, Kevin, et al. "PUSHing core-collapse supernovae to explosions in spherical symmetry. II. explodability and remnant properties." The Astrophysical Journal 870.1 (2018)
- AGILE is described, in complete, in Mattias Liebendorfer's thesis; the ADS record for this reference can be found at: https://ui.adsabs.harvard.edu/abs/2000PhDT.......311L/abstract
