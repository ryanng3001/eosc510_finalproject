# eosc510_finalproject

## update, as of 7 nov (RN)
Explored 18 PCA combinations. They varied according to dataset (field only, incubation only, all), taxonomic ranking (phylum, class, order) and processing (raw abundance, log abundance).
The files *pca_field_RN.ipynb*, *pca_incubation_RN.ipynb* and *pca_all_RN.ipynb* provide code for running pca based on the dataset. For each file, the scatterplot in pc space is plotted. 

Note that within each file, the functions *run_pca* and *run_pca_log* computes the fractional variance, pcs and eigenvectors for different input matrices (raw abundance or log abundance). The motivation is that there are many zeros in the raw abundance data (i.e. many taxa within a sample w/ no abundance). This could mess up the covariance. So what I did was to keep only columns with positive abundance in at least 35% of samples, replace the zeros with a small value, then log the values and subtract by the sample (row) mean before standardizing the data. The idea here is to reflect how much more abundant a taxa is compared to the average. 

Also note that for **field data**, 
- 16 samples
- for raw abundance pca: 100 phylum, 246 class, 600 order
- for log abundance pca: 70 phylum, 151 class, 310 order
- factors of interest: lake, edge, depth 

For **incubation data**, 
- 32 samples
- for raw abundance pca: 100 phylum, 246 class, 600 order
- for log abundance pca: 67 phylum, 144 class, 285 order
- factors of interest: lake, edge, sampling day, temp, sampling time point

For **all data**, 
- 48 samples
- for raw abundance pca: 100 phylum, 246 class, 600 order
- for log abundance pca: 69 phylum, 150 class, 294 order
- **common** factors of interest: lake, edge

*Next: we should probably choose one PCA to work with; I think in general the factors are not very discernable from the PCA but there is evidence of clustering within the PC space. 
So we could choose the PCA which gives the 'best chance' of a good cluster and proceed w/ SOM*
