gutSMASH - A new approach to functionally profile the human microbiome for specialized primary metabolic gene clusters
======================================================================================================================

Anaerobic bacteria in the gut are responsible for the synthesis and transformation of diverse molecules involved in host-microbe and microbe-microbe interactions, that ultimately derive host phenotypes. The pathways encoding the production of these molecules belong to a specialized primary metabolism and are often physically clustered in the genome, in regions also known as metabolic gene clusters (MGCs).

gutSMASH is a tool that has been developed to fulfil the need of systematically evaluating the metabolic potential of these bacteria by predicting both known and novel anaerobic MGCs from the gut microbiome. The gutSMASH detection rules have been validated using a training set presented in our main publication.

Altogether, this new software provides a comprehensive toolkit to functionally characterize anaerobic bacterial genomes by not only predicting MGCs of known functions but also novel MGCs that may represent good candidates for further experimental characterization.

This repository is used to port gutSMASH to be compatible with Python 3, along
with mayor restructuring and code cleanup efforts. It is not feature-compatible
with previous antiSMASH versions for now, and certainly is not
production-quality code.

Development & Funding
---------------------

The development of gutSMASH is a collaboration between the Bioinformatics Department at 
Wageningen University and Research and the Department of Bioengineering at Stanford University. This work has also been possible thanks to the technical support the Novo Nordisk Foundation Center for Biosustainability provided.

How to install gutSMASH
-----------------------

To be able to run gutSMASH, different binaries have to be installed, by either using apt-get install:

```
sudo apt-get install hmmer2 hmmer diamond-aligner fasttree prodigal ncbi-blast+ muscle glimmerhmm
```

or Homebrew for macOS systems:

```
brew install hmmer2 hmmer diamond fasttree prodigal blast muscle brewsci/science/glimmerhmm
```

Assuming python3 is installation, the python3 dependencies can be installed using pip3 with the following command:

```
pip3 install biopython helperlibs bcbio-gff pysvg-py3 scikit-learn matplotlib pyScss Jinja2
```

How to run gutSMASH from the command line
-----------------------------------------

After downloading this gutSMASH git repository the user can run the tool from the command line. The ideal input for gutSMASH is an annotated nucleotide file in Genbank format or EMBL format. Then, the `--minimal` flag has to be included:

```
python3 gutsmash/run_gutsmash.py --minimal gbk_input_file
```

We highly encourge to compare the predicted gene clusters to a database of known and characterized gene clusters using the `--cb-knownclusters`. Also, gene cluster genes can be annotated into different functional categories by using the `-enable-genefunctions` option as follows:

```
python3 gutsmash/run_gutsmash.py --minimal --cb-knownclusters --enable-genefunctions gbk_input_file
```

Alternatively, gutSMASH can also use a fasta file as input. Then, the user has to indicate which gene prediction tool wants to use to annotate the genome using the `--genefinding-tool` option and for instance the `prodigal` tool

```
python3 gutsmash/run_gutsmash.py --genefinding-tool prodigal --cb-knownclusters --enable-genefunctions fasta_input_file
```

See other option available by typing:

```
python3 gutsmash/run_gutsmash.py --help
```

Publications
------------

See http://antismash.secondarymetabolites.org/#!/about for information on citing
gutSMASH.

License
-------

antiSMASH is an open source tool available under the GNU Affero General Public
License version 3.0 or greater. See the [`LICENSE.txt`](LICENSE.txt) file for
details.

Acknowledgements
----------------

Some icons used courtesy of fontawesome.com
