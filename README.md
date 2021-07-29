
<!-- README.md is generated from README.Rmd. Please edit that file -->
# CIDER

<!-- badges: start -->
<!-- badges: end -->
The goal of CIDER is to ...

## Installation

You can install CIDER from [github](https://github.com/zhiyhu/CIDER/) with:

``` r
# install.packages("devtools")
devtools::install_github('zhiyhu/CIDER')
```

## Quick start for evaluating integration resutls

`seu.integrated` is a Seurat object with corrected PCs in `seu.integrated@reductions$pca`.

``` r
library(CIDER)
seu.integrated <- hdbscan.seurat(seu.integrated)
ider <- getIDEr(seu.integrated, verbose = FALSE)
seu.integrated <- estimateProb(seu.integrated, ider)
```

The evaluation scores (IDER-based similarity and empirical p values) can be visualised by

``` r
p1 <- scatterPlot(seu.integrated, "tsne", colour.by = "similarity")
p2 <- scatterPlot(seu.integrated, "tsne", colour.by = "pvalue") 
plot_grid(p1,p2, ncol = 3)
```

![](man/figures/evaluation_scatterplot.png)

## Quick start for asCIDER

``` r
ider <- getIDEr(seu, 
                group.by.var = "initial_cluster",
                batch.by.var = "Batch")
seu <- finalClustering(seu, ider, cutree.h = 0.45)
```

## Quick start for dnCIDER

<!--- You'll still need to render `README.Rmd` regularly, to keep `README.md` up-to-date. `devtools::build_readme()` is handy for this. You could also use GitHub Actions to re-render `README.Rmd` every time you push. An example workflow can be found here: <https://github.com/r-lib/actions/tree/master/examples>.--->
