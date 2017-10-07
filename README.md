# regulon-enrichment
As provided, this code replicates the analysis only from the output of EDGE-pro (after mapping all the reads) through the regulon enrichment test. For convenience, the EDGE-pro output file is provided with this code as deseqFile. You can also download the individual output EDGE-pro files from GEO: GSE104599 (*.rpkm). 

To replicate the regulon enrichment test of the published literature datasets you will need to track down the supplemental data for these publications. See Makefile for expected file names. In the Makefile I have provided a url that works on my machine to the Voskuil et al 2004 dataset but you will have to find the Betts et al 2002 supplement on your own (publisher did not use persistent links). 

You will need to modify the path names for the various applications used in this project. These can be changed by modifying the top few lines of the Makefile.

Run make to reproduce the analysis.

See makefile_dependency_graph.png and makefile_full_dependency_graph.png for a useful graph of the dependecy structure of the Makefile.

If you want make to replicate the read mapping done by EDGE-pro you will need to take the following steps:

1. Uncomment the following two lines from the Makefile: 
#deseqFile: $(SAMPLE_NAMES_WPATH)
#	${EDGE_PRO_FOLDER}/additionalScripts/edgeToDeseq.perl $(SAMPLE_NAMES_WPATH) 

2. Ensure you have EDGE_pro v1.3.1 installed. You will furthermore need to update EDGE_PRO_FOLDER at the top of the Makefile to be the location of these scripts.

3. Download the raw read files from GEO. Update READ_DATA_FOLDER to be the location for all the *.fastq (uncompressed) files.

4. Optional: If you wish to keep the large alignment files (sam format) generated by EDGE_pro out of the default folder you will need to update EDGE_PRO_OUTPUT_FOLDER. You could also make EDGE_PRO_OUTPUT_FOLDER a softlink to an external location.

If you have issues or feedback, please feel free to contact me:

Will Matern
maternwill@gmail.com