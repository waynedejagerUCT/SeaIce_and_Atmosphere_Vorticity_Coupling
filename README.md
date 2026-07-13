# SeaIce_and_Atmosphere_Vorticity_Coupling

This repository contains the code used to produce the Journal of Geophysical Research: Oceans article:

**de Jager, W., & Vichi, M. (2025). Increased rotational coupling between Antarctic sea ice and the atmosphere over the last 30 years. Journal of Geophysical Research: Oceans, 130, e2024JC021239. https://doi.org/10.1029/2024JC021239**

-------
The IceAtmos_anomaly_trends_v002.py script is used to iterate through daily sea-ice displacement estimates (using the EUMETSAT OSI-455-c low resolution sea-ice drift product) to quantify ice field vorticity variables. This script also requires ERA-5 vorticity data at hourly resolutions. These hourly vorticity fields are averaged of the same 24-hr window that the ice drift estimates are made. The ERA-5 fields are interpolated as to match the projection of the sea-ice displacement vectors. A mask is then created such that only atmospheric cells overlying the ice are considered. The script pools daily vorticity for both the ice and atmopshere into annual .csv files.

Script details and parameterization:
* Sectors/Seas are intially defined, as described in Section 2 of manuscript.
* Time0 and Time1 of the displacement tracking window. Defined by the sea-ice drift product and used in ERA-5 data averaging window.
* Vorticity is in units "per second"
* swath_remapping function interpolates the scalar ERA-5 atmospheric data to match the grid and projection of the sea-ice.
* Temporal range. Current set to iterate over entire drift product temporal range (1991-2020).
* Spatial range (can work for both Arctic and Antarctic regions with suitable adjustments made to the boundary parameters)
* Sample radius defines the seaerch radius of the interpolation method, set to 'nearest' by default.
* Strictness of the valid displacement estimates threshold requirement to be consdiered. Det to '20', which implies that only nominal quality estimates are considered, as defined by the OSI-455c product index.

All neccessary python packages are listed in the import list.

-------
The AtmosIceVorticityFieldCorrelation_v003.py script is used to iterate through daily sea-ice displacement estimates (using the EUMETSAT OSI-455-c low resolution sea-ice drift product) to quantify ice field similarity to the atmospheric vorticity field, where similarity is defined as the linear correlation coefficient between the two planes by flattening each into a 1-dimensional array. This script also requires ERA-5 vorticity data at hourly resolutions. These hourly vorticity fields are averaged of the same 24-hr window that the ice drift estimates are made. The ERA-5 fields are interpolated as to match the projection of the sea-ice displacement vectors. A mask is then created such that only atmospheric cells overlying the ice are considered. The script pools daily vorticity for both the ice and atmopshere into annual .csv files.

Script details and parameterization:
* Sectors/Seas are intially defined, as described in Section 2 of manuscript.
* Time0 and Time1 of the displacement tracking window. Defined by the sea-ice drift product and used in ERA-5 data averaging window.
* Vorticity is in units "per second"
* swath_remapping function interpolates the scalar ERA-5 atmospheric data to match the grid and projection of the sea-ice.
* Temporal range. Current set to iterate over entire drift product temporal range (1991-2020).
* Spatial range (can work for both Arctic and Antarctic regions with suitable adjustments made to the boundary parameters)
* Sample radius defines the seaerch radius of the interpolation method, set to 'nearest' by default.
* Strictness of the valid displacement estimates threshold requirement to be consdiered. Det to '20', which implies that only nominal quality estimates are considered, as defined by the OSI-455c product index.
* A linear correlation coefficient is computed from daily field overlaps over the course of each month, meaning every cell of every day is compared against its corresponding cell in the atmosphere.

All neccessary python packages are listed in the import list.
