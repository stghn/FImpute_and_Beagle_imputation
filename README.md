# Imputation
Genotype imputation bash script for BEAGLE v3, v4 & v4.1 and FImpute software.  
The bash script uses PLINK format data and PLINK software itself to undertake most of the task.

## Imputation with FImpute
There are two bash scripts for using FImpute software.  
### A) _FIminor.sh_   
This is to run minor imputation on a (one) dataset with few markers missing for some few individuals

### B) _FImajor.sh_  
This is to run major imputation on two different SNP chips (Eg. Impute 50k to HD or 7k to 50k etc)

## Running the FIminor.sh script to undertake MINOR imputation with FIMPUTE  
This script (***FIminor.sh***) requires the below arguments:  
1. **Reference file** (The file should be a PLINK binary file with alleles coded as 11, 12, 22)  
2. **Output name of Reference file**  
3. **Output name of final file after imputation**  
4. **Output genotype format** (either plink or genotypes format) 
5. **Allelecode**  
6. **Pedigree information** (Optional -- with Progeny, Sire, Dam, Sex) 
          
The final output is a **plink binary file** with its prefix as argument and **_imp**.  

## Running FImajor.sh script to undertake MAJOR imputation with FIMPUTE  
This script (***FImajor.sh***) requires the below arguments:   
1. **Reference file** (The file should be a PLINK binary file with alleles coded as 11, 12, 22)  
2. **Output name of Reference file**  
3. **Validation file** - The file to be imputed (The file should be a PLINK binary file with alleles coded as 11, 12, 22)  
4. **Output name of file to be imputed**
5. **Output name of final file after imputation**  
6. **Where R is located**  
7. **Output genotype format** (either plink or genotype format)  
8. **Allelecode**  
9. **Pedigree information** (is "Optional" -- if provided, it should have 4 columns -- Progeny, Sire, Dam, Sex)  
         
The final output is a **plink binary file** with its prefix as argument and suffix as **_imp.bed**, **_imp.bim** and **_imp.fam**.  

## Running the Example files using FIminor.sh and FImajor.sh scripts
### Examples for minor imputation (FIminor.sh)  

**Without Pedigree information**  
```sh
./FIminor.sh Example/ex01_ref ref resultsREF plink 12 
```

**With Pedigree information**  
```sh
./FIminor.sh Example/ex01_ref ref resultsREF plink 12 Example/ex01.dat  
```
**OUTPUT file-names**  
```sh
resultsREF_imp.bim  resultsREF_imp.bed  resultsREF_imp.fam  
```
### Examples for minor imputation (FImajor.sh)
**Without Pedigree information**
```sh
./FImajor.sh Example/ex01_ref REF Example/ex01_valldchip val resultsVAL /usr/bin/Rscript plink 12
```

**With Pedigree information** 
```sh
./FImajor.sh Example/ex01_ref REF Example/ex01_valldchip val resultsVAL /usr/bin/Rscript plink 12 Example/ex01.dat
```

**OUTPUT file-names**  
```sh
imp7kto50k_imp.bim imp7kto50k_imp.bed imp7kto50k_imp.fam  
```

**To get help for parameters to run for each script type the following:**  
```sh
./FIminor.sh help  
./FImajor.sh help  
```
-----
## Imputation with BEAGLEv4 and BEAGLE v4.1

There are two bash scripts for using Beagle software version 4 and 4.1  
### A) _BGLminor.sh_ or _BGLminor4n1.sh_
This is to run minor imputation on a (one) dataset with few markers missing for some individuals  

### B) _BGLmajor.sh_  or _BGLmajor4n1.sh_ 
This is to run major imputation on two different SNP chips. (Eg. Impute 50k to HD or 7k to 50k etc)  

Get help by runing the following: (The parameters needed to run the script will be printed out)  
./BGLminor.sh help  
./BGLmajor.sh help  

### Running _BGLminor.sh_ or _BGLminor4n1.sh_ script to undertake MINOR imputation with BEAGLE v4 & v4.1 
The script (**_BGLminor.sh_** or **_BGLminor4n1.sh_**) requires the below arguments:  
1. **Reference file** (The file should be a PLINK binary file with alleles coded as 11-12-22 or AA-AB-BB)  
2. **Output name of Reference file**  
3. **Output name of final file after imputation**  
4. **Start of chromosome**  
5. **End of chromosome**  
6. **Allelecode**
        
The final output is a **plink binary** file with its prefix as argument and suffix as **_imp.bed**, **_imp.bim** and **_imp.fam**. It also generates a folder called **interMS-summary** which contains **imputation per chromosome and other important output of BEAGLE**.


### Running _./BGLmajor.sh_ or _./BGLmajor4n1.sh_ script to undertake MAJOR imputation with BEAGLE v4 & v4.1  
The script (**_BGLmajor.sh_** or **_BGLmajor4n1.sh_**) requires the below arguments:  
1. **Reference file** (The file should be a PLINK binary file with alleles coded as 11, 12, 22)  
2. **Output name of Reference file**  
3. **Validation file** - The file to be imputed (The file should be a PLINK binary file with alleles coded as 11, 12, 22)  
4. **Output name of file to be imputed**  
5. **Output name of final file after imputation**  
6. **Start of chromosome**  
7. **End of chromosome**  
8. **Allelecode**

The final output is a **plink binary** file with its prefix as argument and suffix as **_imp.bed**, **_imp.bim** and **_imp.fam**. It also generates a folder called **interMS-summary** which contains **imputation per chromosome and other important output of BEAGLE**.


##  Running the Example files
### Examples for minor imputation (BGLminor.sh or BGLminor4n1.sh)
**For one chromosome ONLY**
```sh
./BGLminor.sh Example/ex01_ref ex01ref resultsREF 1 1 12
```
**For a range of chromosomes**
```sh
./BGLminor.sh Example/ex01_ref ex01ref resultsREF 25 29
```
**For all chromosomes**
```sh
./BGLminor Example/ex01_ref ex01ref resultsREF 1 29
```
**OUTPUT file-names**  
```sh
resultsREF_imp.bim  resultsREF_imp.bed  resultsREF_imp.fam
```
### Examples for minor imputation (BGLmajor.sh or BGLmajor4n1.sh)
**For one chromosome ONLY**
```sh
./BGLmajor.sh Example/ex01_ref ex01ref Example/ex01_valldchip ex01val resultsldchip 25 25 12
```
**For a range of chromosomes**
```sh
./BGLmajor.sh Example/ex01_ref ex01ref Example/ex01_valldchip ex01val resultsldchip 1 2 12
```
**For all chromosomes**
```sh
./BGLmajor.sh Example/ex01_ref ex01ref Example/ex01_valldchip ex01val resultsldchip 1 29 12
```
**OUTPUT file-names**  
```sh
resultsldchip_imp.bim  resultsldchip_imp.bed  resultsldchip_imp.fam  
```

