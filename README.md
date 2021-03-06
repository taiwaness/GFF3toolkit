# GFF3toolkit - Python programs for processing GFF3 files
* Current functions
    - [Detect GFF3 format errors](#detect-gff3-format-errors-back)
    - [Merge two GFF3 files](#merge-two-gff3-files-back)
    - [Sort a GFF3 file](#sort-a-gff3-file-back)
    - [Generate biological sequences from a GFF3 file](#generate-biological-sequences-from-a-gff3-file-back)

## Background

The [GFF3 format](https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md) (Generic Feature Format Version 3) is one of the standard formats to describe and represent genomic features. It is an incredibly flexible, 9-column format, which is easily manipulated by biologists. This flexibility, however, makes it very easy to break the format. We have developed the GFF3toolkit to help identify common problems with GFF3 files; sort GFF3 files (which can aid in using down-stream processing programs and custom parsing); merge two GFF3 files into a single, non-redundant GFF3 file; and generate FASTA files from a GFF3 file for many use cases (e.g. feature types beyond mRNA).

[Frequently Asked Questions/FAQ](https://github.com/NAL-i5K/GFF3toolkit/wiki/FAQ) 

## Detect GFF3 format errors ([back](#gff3toolkit---python-programs-for-processing-gff3-files))

* bin/gff-QC.py - Detection of GFF format errors (~50 types of errors).
    - [gff-QC.py readme](gff-QC.md)
    - [gff-QC.py full documentation](https://github.com/NAL-i5K/GFF3toolkit/wiki/Detection-of-GFF3-format-errors)
    - Quick start:
        `python2.7 GFF3toolkit/bin/gff-QC.py -g GFF3toolkit/example_file/example.gff3 -f GFF3toolkit/example_file/reference.fa -o test2.txt`
    - Please refer to lib/ERROR/ERROR.py to see the full list of Error codes and the corresponding Error tags.

## Merge two GFF3 files ([back](#gff3toolkit---python-programs-for-processing-gff3-files))

* bin/gff3-merge.py - Merge two GFF3 files
    - [gff3-merge.py readme](gff3-merge.md)
    - [gff3-merge.py full documentation](https://github.com/NAL-i5K/GFF3toolkit/wiki/Merge-two-GFF3-files)
    - Quick start:
        - Merge the two file with auto-assignment of replace tags (default)
            `python2.7 GFF3toolkit/bin/gff3-merge.py -g1 GFF3toolkit/example_file/new_models.gff3 -g2 GFF3toolkit/example_file/reference.gff3 -f GFF3toolkit/example_file/reference.fa -og merged.gff -r merged_report.txt`
        - If your gff files have assigned proper replace tags at column 9 (Format: replace=[Transcript ID]), you could merge the two gff files wihtout auto-assignment of tags.
            `python2.7 GFF3toolkit/bin/gff3-merge.py -g1 GFF3toolkit/example_file/new_models.gff3 -g2 GFF3toolkit/example_file/reference.gff3 -f GFF3toolkit/example_file/reference.fa -og merged.gff -r merged_report.txt -noAuto`

## Sort a GFF3 file ([back](#gff3toolkit---python-programs-for-processing-gff3-files))

* bin/gff3_sort.py - Sort a GFF3 file according to the order of Scaffold, coordinates on a Scaffold, and parent-child feature relationships
    - [gff3_sort.py readme](gff3-sort.md)
    - Quick start:
        `python2.7 GFF3toolkit/bin/gff3_sort.py -g GFF3toolkit/example_file/example.gff3 -og example-sorted.gff3`

## Generate biological sequences from a GFF3 file ([back](#gff3toolkit---python-programs-for-processing-gff3-files))

* bin/gff3_to_fasta.py - extract biological sequences (such as spliced transcripts, cds, or peptides) from specific regions of genome based on a GFF3 file
    - [gff3_to_fasta.py readme](gff3_to_fasta.md)
    - Quick start:
        `python2.7 GFF3toolkit/bin/gff3_to_fasta.py -g GFF3toolkit/example_file/example.gff3 -f GFF3toolkit/example_file/reference.fa -st all -d simple -o test_sequences`

## Example Files ([back](#gff3toolkit---python-programs-for-processing-gff3-files))

* example_file/
    - Example files for testing

## Internal Dependencies ([back](#gff3toolkit---python-programs-for-processing-gff3-files))
* [lib/gff3_modified](lib/gff3_modified)/
    - Basic data structure used for nesting the information of genome annotations in GFF3 format.
* [lib/gff3_to_fasta](lib/gff3_to_fasta)/
    - Extract specific sequences from genome sequences according to the GFF3 file.
* [lib/ERROR](lib/ERROR)
    - Contains the full list of Error codes and the corresponding Error tag
* [lib/function4gff](lib/function4gff)/
    - Functions for gff3 processing
* lib/gff3.py
    - This program was contributed by Han Lin (http://gff3-py.readthedocs.org/en/latest/readme.html). Code was modified for customized usage.
* [lib/inter_model](lib/inter_model)/
    - QC functions for processing multiple features between models (inter-model) in a GFF3 file.
* [lib/intra_model](lib/intra_model)/
    - QC functions for processing multiple features within a model (intra-model) in a GFF3 file.
* [lib/single_feature](lib/single_feature)/
    - QC functions for processing single features in a GFF3 file.
