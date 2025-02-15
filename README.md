# 2019 Genomic Epidemiology Workshop

### NGS Variant Annotation: Hands-on session
---
* Date: 2019.8.5-9
* Place: Genomics Research Center, Academia Sinica
* Register URL: https://gew2019.genomics.sinica.edu.tw/
* Software download
    * URL: http://annovar.openbioinformatics.org/en/latest/

* Raw data
    * gatk.vcf (reference hg38)
    * demo_sample.vcf.gz (Ogden Syndrome, reference hg19)
    

* Result
    * HG00403.chr20.gatk.hg38_multianno.txt
    * HG00403.chr20.gatk.hg38_multianno.xlsx


### Download Annovar db

```bash
$ ./annovar_db_download.sh
```

### VCF to Annovar input format

```bash
$ convert2annovar.pl -format vcf4 gatk.vcf > HG00403.chr20.gatk.avinput
```
```bash
NOTICE: Finished reading 3481 lines from VCF file
NOTICE: A total of 3443 locus in VCF file passed QC threshold, representing 3105 SNPs (2069 transitions and 1036 transversions) and 338 indels/substitutions
NOTICE: Finished writing 3105 SNP genotypes (2069 transitions and 1036 transversions) and 338 indels/substitutions for 1 sample
```

### Run Annovar table function

* script
* 
```bash
$ perl annovar.pl -t 10 -i HG00403.chr20.gatk.avinput -r hg38 -o HG00403.chr20.gatk
```

* tab output
```bash
$ table_annovar.pl HG00403.chr20.gatk.avinput $HOME/humandb/ -buildver hg38 -out HG00403.chr20.gatk -remove -protocol refGene,ensGene,cytoBand,genomicSuperDups,gwasCatalog,avsnp150,esp6500siv2_all,1000g2015aug_all,1000g2015aug_afr,1000g2015aug_amr,1000g2015aug_eur,1000g2015aug_eas,1000g2015aug_sas,nci60,cosmic89_coding,cosmic89_noncoding,clinvar_20190305,gnomad_genome,gnomad211_exome,exac03,intervar_20180118,dbnsfp31a_interpro -operation g,g,r,r,r,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f -otherinfo -nastring NA
```

* csv output
```bash
$ table_annovar.pl HG00403.chr20.gatk.avinput $HOME/humandb/ -buildver hg38 -out HG00403.chr20.gatk -remove -protocol refGene,ensGene,cytoBand,genomicSuperDups,gwasCatalog,avsnp150,esp6500siv2_all,1000g2015aug_all,1000g2015aug_afr,1000g2015aug_amr,1000g2015aug_eur,1000g2015aug_eas,1000g2015aug_sas,nci60,cosmic89_coding,cosmic89_noncoding,clinvar_20190305,gnomad211_genome,gnomad211_exome,exac03,intervar_20180118,dbnsfp31a_interpro, -operation g,g,r,r,r,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f,f -otherinfo -nastring . -csvout
```

### Easy Run Annovar talbe function
```bash
$ perl annovar.pl -t 10 -i demo_sample.avinput -r hg19 -o demo_sample
```

* **Gene-based (g)**
    * refGene
    * ensGene

* **Region-based (r)**
    * cytoBand
    * genomicSuperDups
    * gwasCatalog

* **Filter-based (f)**
    * avsnp150
    * esp6500siv2_all
    * 1000g2015aug_all
    * 1000g2015aug_afr
    * 1000g2015aug_amr
    * 1000g2015aug_eur
    * 1000g2015aug_eas
    * 1000g2015aug_sas
    * gnomad211_genome
    * gnomad211_exome
    * nci60
    * cosmic85
    * clinvar_20190305
    * exac03
    * intervar_20180118
    * dbnsfp31a_interpro


### Processing Information
```bash
-----------------------------------------------------------------
NOTICE: Processing operation=g protocol=refGene

NOTICE: Running with system command <annotate_variation.pl -geneanno -buildver hg38 -dbtype refGene -outfile HG00403.chr20.gatk.refGene -exonsort HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Output files were written to HG00403.chr20.gatk.refGene.variant_function, HG00403.chr20.gatk.refGene.exonic_variant_function
NOTICE: the queryfile contains 3443 lines
NOTICE: threading is disabled for gene-based annotation on file with less than 1000000 input lines
NOTICE: Reading gene annotation from /home/philippe/humandb/hg38_refGene.txt ... Done with 71041 transcripts (including 17412 without coding sequence annotation) for 27813 unique genes
NOTICE: Processing next batch with 3443 unique variants in 3443 input lines
NOTICE: Reading FASTA sequences from /home/philippe/humandb/hg38_refGeneMrna.fa ... Done with 7 sequences
WARNING: A total of 515 sequences will be ignored due to lack of correct ORF annotation
-----------------------------------------------------------------
NOTICE: Processing operation=g protocol=ensGene

NOTICE: Running with system command <annotate_variation.pl -geneanno -buildver hg38 -dbtype ensGene -outfile HG00403.chr20.gatk.ensGene -exonsort HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Output files were written to HG00403.chr20.gatk.ensGene.variant_function, HG00403.chr20.gatk.ensGene.exonic_variant_function
NOTICE: the queryfile contains 3443 lines
NOTICE: threading is disabled for gene-based annotation on file with less than 1000000 input lines
NOTICE: Reading gene annotation from /home/philippe/humandb/hg38_ensGene.txt ... Done with 89732 transcripts (including 28806 without coding sequence annotation) for 42087 unique genes
NOTICE: Processing next batch with 3443 unique variants in 3443 input lines
NOTICE: Reading FASTA sequences from /home/philippe/humandb/hg38_ensGeneMrna.fa ... Done with 13 sequences
WARNING: A total of 361 sequences will be ignored due to lack of correct ORF annotation
-----------------------------------------------------------------
NOTICE: Processing operation=r protocol=cytoBand

NOTICE: Running with system command <annotate_variation.pl -regionanno -dbtype cytoBand -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Output file is written to HG00403.chr20.gatk.hg38_cytoBand
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 338 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_cytoBand.txt ... Done with 1433 regions
NOTICE: Finished region-based annotation on 345 genetic variants
-----------------------------------------------------------------
NOTICE: Processing operation=r protocol=genomicSuperDups

NOTICE: Running with system command <annotate_variation.pl -regionanno -dbtype genomicSuperDups -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Output file is written to HG00403.chr20.gatk.hg38_genomicSuperDups
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 338 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_genomicSuperDups.txt ... Done with 69894 regions
NOTICE: Finished region-based annotation on 345 genetic variants
-----------------------------------------------------------------
NOTICE: Processing operation=r protocol=gwasCatalog

NOTICE: Running with system command <annotate_variation.pl -regionanno -dbtype gwasCatalog -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Output file is written to HG00403.chr20.gatk.hg38_gwasCatalog
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Finished region-based annotation on 338 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Finished region-based annotation on 345 genetic variants
NOTICE: Reading annotation database /home/philippe/humandb/hg38_gwasCatalog.txt ... Done with 152384 regions
NOTICE: Finished region-based annotation on 345 genetic variants
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=avsnp150

NOTICE: Running system command <annotate_variation.pl -filter -dbtype avsnp150 -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_avsnp150_dropped, other variants are written to HG00403.chr20.gatk.hg38_avsnp150_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 310
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 313
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 300
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 310
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 321
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 318
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 297
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 315
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 297
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
NOTICE: Database index loaded. Total number of bins is 28304406 and the number of bins to be scanned is 303
NOTICE: Scanning filter database /home/philippe/humandb/hg38_avsnp150.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=esp6500siv2_all

NOTICE: Running system command <annotate_variation.pl -filter -dbtype esp6500siv2_all -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: the --dbtype esp6500siv2_all is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_esp6500siv2_all_dropped, other variants are written to HG00403.chr20.gatk.hg38_esp6500siv2_all_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 3
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 5
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 7
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 12
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 4
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
NOTICE: Database index loaded. Total number of bins is 683825 and the number of bins to be scanned is 2
NOTICE: Scanning filter database /home/philippe/humandb/hg38_esp6500siv2_all.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_all

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_all -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_ALL.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_ALL.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 178
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 222
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 174
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 199
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 188
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 201
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 236
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 195
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 210
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2821635 and the number of bins to be scanned is 208
NOTICE: Scanning filter database /home/philippe/humandb/hg38_ALL.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_afr

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_afr -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_AFR.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_AFR.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 178
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 201
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 195
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 222
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 187
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 236
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 210
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 207
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 199
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2817370 and the number of bins to be scanned is 174
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AFR.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_amr

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_amr -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_AMR.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_AMR.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 177
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 222
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 201
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 199
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 187
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 195
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 210
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 207
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 236
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2812567 and the number of bins to be scanned is 174
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_AMR.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_eur

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_eur -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_EUR.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_EUR.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 178
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 188
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 195
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 201
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 199
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 210
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 236
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 222
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 208
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2809469 and the number of bins to be scanned is 174
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EUR.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_eas

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_eas -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_EAS.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_EAS.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 201
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 210
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 174
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 222
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 187
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 199
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 178
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 236
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 207
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2810247 and the number of bins to be scanned is 195
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_EAS.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=1000g2015aug_sas

NOTICE: Running system command <annotate_variation.pl -filter -dbtype 1000g2015aug_sas -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_SAS.sites.2015_08_dropped, other variants are written to HG00403.chr20.gatk.hg38_SAS.sites.2015_08_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 174
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 207
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 222
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 186
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 178
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 195
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 210
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 199
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 201
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
NOTICE: Database index loaded. Total number of bins is 2813352 and the number of bins to be scanned is 236
NOTICE: Scanning filter database /home/philippe/humandb/hg38_SAS.sites.2015_08.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=nci60

NOTICE: Running system command <annotate_variation.pl -filter -dbtype nci60 -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: the --dbtype nci60 is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_nci60_dropped, other variants are written to HG00403.chr20.gatk.hg38_nci60_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 17
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 5
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 2
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 12
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 11
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
NOTICE: Database index loaded. Total number of bins is 81459 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_nci60.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=cosmic89_coding

NOTICE: Running system command <annotate_variation.pl -filter -dbtype cosmic89_coding -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: the --dbtype cosmic89_coding is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_cosmic89_coding_dropped, other variants are written to HG00403.chr20.gatk.hg38_cosmic89_coding_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_coding.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=cosmic89_noncoding

NOTICE: Running system command <annotate_variation.pl -filter -dbtype cosmic89_noncoding -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10>
NOTICE: the --dbtype cosmic89_noncoding is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_cosmic89_noncoding_dropped, other variants are written to HG00403.chr20.gatk.hg38_cosmic89_noncoding_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_cosmic89_noncoding.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=clinvar_20190305
NOTICE: Finished reading 5 column headers for '-dbtype clinvar_20190305'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype clinvar_20190305 -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype clinvar_20190305 is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_clinvar_20190305_dropped, other variants are written to HG00403.chr20.gatk.hg38_clinvar_20190305_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 8
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 21
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 3
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 7
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 12
NOTICE: Database index loaded. Total number of bins is 46038 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_clinvar_20190305.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=gnomad211_genome
NOTICE: Finished reading 17 column headers for '-dbtype gnomad211_genome'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype gnomad211_genome -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype gnomad211_genome is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_gnomad211_genome_dropped, other variants are written to HG00403.chr20.gatk.hg38_gnomad211_genome_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 309
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 321
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 318
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 297
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 303
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 300
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 315
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 297
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 310
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
NOTICE: Database index loaded. Total number of bins is 28076758 and the number of bins to be scanned is 313
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_genome.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=gnomad211_exome
NOTICE: Finished reading 17 column headers for '-dbtype gnomad211_exome'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype gnomad211_exome -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype gnomad211_exome is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_gnomad211_exome_dropped, other variants are written to HG00403.chr20.gatk.hg38_gnomad211_exome_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 3
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 3
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 9
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 4
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
NOTICE: Database index loaded. Total number of bins is 771804 and the number of bins to be scanned is 9
NOTICE: Scanning filter database /home/philippe/humandb/hg38_gnomad211_exome.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=exac03
NOTICE: Finished reading 8 column headers for '-dbtype exac03'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype exac03 -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype exac03 is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_exac03_dropped, other variants are written to HG00403.chr20.gatk.hg38_exac03_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 8
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 4
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 9
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 3
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 1
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Database index loaded. Total number of bins is 749044 and the number of bins to be scanned is 3
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_exac03.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=intervar_20180118
NOTICE: Finished reading 29 column headers for '-dbtype intervar_20180118'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype intervar_20180118 -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype intervar_20180118 is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_intervar_20180118_dropped, other variants are written to HG00403.chr20.gatk.hg38_intervar_20180118_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 6
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 4
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 1
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 2
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 2
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 2
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Database index loaded. Total number of bins is 535845 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_intervar_20180118.txt...Done
-----------------------------------------------------------------
NOTICE: Processing operation=f protocol=dbnsfp31a_interpro
NOTICE: Finished reading 1 column headers for '-dbtype dbnsfp31a_interpro'

NOTICE: Running system command <annotate_variation.pl -filter -dbtype dbnsfp31a_interpro -buildver hg38 -outfile HG00403.chr20.gatk HG00403.chr20.gatk.avinput /home/philippe/humandb/ -thread 10 -otherinfo>
NOTICE: the --dbtype dbnsfp31a_interpro is assumed to be in generic ANNOVAR database format
NOTICE: Variants matching filtering criteria are written to HG00403.chr20.gatk.hg38_dbnsfp31a_interpro_dropped, other variants are written to HG00403.chr20.gatk.hg38_dbnsfp31a_interpro_filtered
NOTICE: the queryfile contains 3443 lines
NOTICE: Creating new threads for query line 1 to 345
NOTICE: Creating new threads for query line 346 to 690
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 691 to 1035
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1036 to 1380
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1381 to 1725
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 1726 to 2070
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2071 to 2415
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2416 to 2760
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 2761 to 3105
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Creating new threads for query line 3106 to 3443
NOTICE: Processing next batch with 345 unique variants in 345 input lines
NOTICE: Processing next batch with 338 unique variants in 338 input lines
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 0
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 1
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 1
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 3
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 1
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Database index loaded. Total number of bins is 275396 and the number of bins to be scanned is 0
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
NOTICE: Scanning filter database /home/philippe/humandb/hg38_dbnsfp31a_interpro.txt...Done
-----------------------------------------------------------------
NOTICE: Multianno output file is written to HG00403.chr20.gatk.hg38_multianno.csv
Finished
```

---

### Database download log
```bash
./annovar_db_download.sh
```

```bash
Create humandb folder done!
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_refGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_refGeneMrna.fa.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_refGeneVersion.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_refGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_refGeneMrna.fa.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_refGeneVersion.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_knownGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_kgXref.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_knownGeneMrna.fa.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_knownGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_kgXref.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_knownGeneMrna.fa.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_ensGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_ensGeneMrna.fa.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_ensGene.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_ensGeneMrna.fa.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://hgdownload.cse.ucsc.edu/goldenPath/hg19/database/cytoBand.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
--2018-08-06 17:58:27--  http://hgdownload.cse.ucsc.edu/goldenpath/hg38/database/cytoBand.txt.gz
Resolving hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)... 128.114.119.163
Connecting to hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)|128.114.119.163|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9882 (9.7K) [application/x-gzip]
Saving to: ‘cytoBand.txt.gz’

cytoBand.txt.gz                              100%[============================================================================================>]   9.65K  --.-KB/s    in 0s

2018-08-06 17:58:27 (204 MB/s) - ‘cytoBand.txt.gz’ saved [9882/9882]

NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://hgdownload.cse.ucsc.edu/goldenPath/hg19/database/genomicSuperDups.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
--2018-08-06 17:58:34--  http://hgdownload.cse.ucsc.edu/goldenpath/hg38/database/genomicSuperDups.txt.gz
Resolving hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)... 128.114.119.163
Connecting to hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)|128.114.119.163|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4202400 (4.0M) [application/x-gzip]
Saving to: ‘genomicSuperDups.txt.gz’

genomicSuperDups.txt.gz                      100%[============================================================================================>]   4.01M   685KB/s    in 7.0s

2018-08-06 17:58:41 (583 KB/s) - ‘genomicSuperDups.txt.gz’ saved [4202400/4202400]

NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://hgdownload.cse.ucsc.edu/goldenPath/hg19/database/phastConsElements100way.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
--2018-08-06 17:59:04--  http://hgdownload.cse.ucsc.edu/goldenpath/hg38/database/phastConsElements100way.txt.gz
Resolving hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)... 128.114.119.163
Connecting to hgdownload.cse.ucsc.edu (hgdownload.cse.ucsc.edu)|128.114.119.163|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90172140 (86M) [application/x-gzip]
Saving to: ‘phastConsElements100way.txt.gz’

phastConsElements100way.txt.gz               100%[============================================================================================>]  85.99M  14.4MB/s    in 18s

2018-08-06 17:59:22 (4.86 MB/s) - ‘phastConsElements100way.txt.gz’ saved [90172140/90172140]

NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_1000g2015aug.zip ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_1000g2015aug.zip ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_avsnp150.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_avsnp150.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_avsnp150.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_avsnp150.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_nci60.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_nci60.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_nci60.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_nci60.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_clinvar_20180603.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_clinvar_20180603.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_clinvar_20180603.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_clinvar_20180603.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_gnomad_genome.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_gnomad_genome.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_gnomad_genome.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_gnomad_genome.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_gnomad_exome.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_gnomad_exome.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_gnomad_exome.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_gnomad_exome.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_exac03.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_exac03.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_exac03.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_exac03.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_esp6500siv2_all.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_esp6500siv2_all.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_esp6500siv2_all.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_esp6500siv2_all.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_intervar_20180118.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_intervar_20180118.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_intervar_20180118.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_intervar_20180118.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the '/home/philippe/humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_dbnsfp31a_interpro.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg19_dbnsfp31a_interpro.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the 'humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_dbnsfp31a_interpro.txt.gz ... OK
NOTICE: Downloading annotation database http://www.openbioinformatics.org/annovar/download/hg38_dbnsfp31a_interpro.txt.idx.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the 'humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://hgdownload.cse.ucsc.edu/goldenPath/hg19/database/gwasCatalog.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg19 build version, with files saved at the 'humandb' directory
NOTICE: Web-based checking to see whether ANNOVAR new version is available ... Done
NOTICE: Downloading annotation database http://hgdownload.cse.ucsc.edu/goldenPath/hg38/database/gwasCatalog.txt.gz ... OK
NOTICE: Uncompressing downloaded files
NOTICE: Finished downloading annotation files for hg38 build version, with files saved at the 'humandb' directory
```
---

* Reference by:
    * [ANNOVAR](http://annovar.openbioinformatics.org/en/latest/)
    * [Using VAAST to Identify an X-Linked Disorder Resulting in Lethality in Male Infants Due to N-Terminal Acetyltransferase Deficiency](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3135802/)
    * [ANNOVAR: functional annotation of genetic variants from high-throughput sequencing data](http://www.ncbi.nlm.nih.gov/pubmed/20601685)
    * [Genomic variant annotation and prioritization with ANNOVAR and wANNOVAR](http://www.nature.com/nprot/journal/v10/n10/full/nprot.2015.105.html)
    * [NAA10 / rs387906701](http://www.ncbi.nlm.nih.gov/projects/SNP/snp_ref.cgi?rs=rs387906701)
    * [SNPedia](http://snpedia.com/index.php/Rs387906701)
    * [NAA10 mutation causing a novel intellectual disability syndrome with Long QT due to N-terminal acetyltransferase impairment](http://www.nature.com/articles/srep16022)
    * [OMIM - Ogden Syndrome](http://www.omim.org/entry/300855)


* All Information 2019 Genomic Epidemiology Workshop Use
* Edit by [Philippe](http://github.com/geniusphil)