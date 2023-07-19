# README #

### A snakmake pipeline for processing bulk RNA-seq data from [PMID:xxx](https://doi.org/10.1016/j.jbc.2023.105062) ###
- This repo allows to perform bulk RNA-seqe analysis of transcriptome profiling done K562 as reported in this [paper](https://doi.org/10.1016/j.jbc.2023.105062)
 - The K562 transcriptome are generated in K562 cells with the following conditions
   - ctrl -> control cell lines (treated with control siRNA)
   - KD -> endogenous MYB KD (treated with siU2992)
   - MYB Rescue -> rescue of endogenous MYB KD with ectopic expression of N-terminal TY1-tagged MYB
   - D152V Rescue -> rescue of endogenous MYB KD with ectopic expression of N-terminal TY1-tagged MYB with D152V mutation (that abrogates pioneering property of MYB)
   - 2KR Rescue -> rescue of endogenous MYB KD with ectopic expression of N-terminal TY1-tagged MYB with K503R and K527R mutations (that abrogates SUMO conjugation from MYB)
   - ANAA Rescue -> rescue of endogenous MYB KD with ectopic expression of N-terminal TY1-tagged MYB with V267NIV to A267NAA mutation (that abrogates SUMO binding from MYB)
- The transcriptome data for ctrl, KD, MYB rescue and D152V rescue can be found from GEO with accession ID: [GSE85187](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE85187)
- The transcriptome data for 2KR rescue and ANNA rescue can be found from GEO with accession ID: [GSE124542](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE124542)


### How do I get set up? ###

* clone the repo by typing

```
git clone git@github.com:rblemma/K562_Myb_ChIP-seq.git
```
### Configuration ###
- add the required data as follows
- downlod all associated raw fastq file from GEO with accession IDs: GSE85187 and GSE124542 and place it in `../data/0_raw_data` folder and rename accordingly
- ctrl_1: Control replicate 1
- ctrl_2: Control replicate 2
- ctrl_3: Control replicate 3
- KD_1: knockdown replicate 1
- KD_2: knockdown replicate 2
- KD_3: knockdown replicate 3
- WT-MYB_1: Rescue with wildtype MYB replicate 1
- WT-MYB_2: Rescue with wildtype MYB replicate 2
- WT-MYB_3: Rescue with wildtype MYB replicate 3
- D152V_1: Rescue with D152V MYB replicate 1
- D152V_2: Rescue with D152V MYB replicate 2
- D152V_3: Rescue with D152V MYB replicate 3
- 2KR_1: Rescue with 2KR MYB replicate 1
- 2KR_2: Rescue with 2KR MYB replicate 2
- 2KR_3: Rescue with 2KR MYB replicate 3
- ANAA_1: Rescue with ANAA MYB replicate 1
- ANAA_2: Rescue with ANAA MYB replicate 2
- ANAA_3: Rescue with ANAA MYB replicate
- download PhIX sequence (RefSeq: NC 001422.1) in fasta format and store as `data/ref/Phix.fa`
- download specific source file for different required (see the 'Dependencies' section) programs and store them in `../SRC` folder
- download the human GRCH38 reference cdna from Ensembl and store in `../data/ref/ensembl/cdna`
- download the human GRCH38 reference genome from ensemble and build with `bowtie2` to have a structure as follows

`../data/ref/ensembl/bowtie2-index/` to acheive this type the following commands

```
bowtie2-build [options]* <reference_in> <bt2_base>
```

### Dependencies ###
- Snakemkae >= 3.5
- fastqc (version 0.11.2)
- trimmomatic (version 0.36)
- BBMap (version 37.4)
- Tophat2 (version 2.1.1)
- picard-tool (version 2.10.4)
- bowtie2 (version 2.2.9)
- cufflinks suite (version 2.2.1)
- CummeRbund R package (version 2.16)

### How to run tests ###
- Type the following from the `results` folder
- you can increase the number of cores you want to use by assigning a number to the -j parameter. The following command uses 1 core

```
snakemake -j 1
```

### Who do I talk to? ###

* Roza Berhanu Lemma (rozaberhanu@gmail.com)
