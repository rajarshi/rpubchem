Allows you to access [PubChem](https://pubchem.ncbi.nlm.nih.gov/) structures and bioassay data. The package supports retrieval of any AID (even primary screens, though this can be quite slow) or subsets of a screen by CID or SID. To install
```R
library(devtools)
install_github("CDK-R/rpubchem", dependencies=TRUE)
```
Once installed you can retrieve assays using the `get.assay` method:
```R
## Retrieve the whole of AID 2044
dat <- get.assay(2044)

## Retrieve data for CIDs 644411, 645075 and 645739 from AID 361 (a large screen with 50K compounds)
dat <- get.assay(361, cid=c(644411,645075,645739), quiet=FALSE)
```
You can search for assays using text search as well as obtain the description (which actually includes the description, comments and column types) for an assay by AID. In addition to the description, we can obtain the summary section, which includes, among other things, counts of actives, inactives and so on
```R
## find assay ID's related to yeast
aids <- find.assay.id('yeast')

## get the description of the first 10 assays
descs <- sapply( lapply(aids[1:10], get.assay.desc), function(x) x$assay.desc )

## get assay summary for the first one
get.assay.summary(aids[1])
```
  
