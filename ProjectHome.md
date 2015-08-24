This project addresses the following problem: Given a dataset of sparse vector data,  find all similar vector pairs according to a similarity function such as cosine distance and a given similarity score threshold.  (This problem is also known as the "similarity join.")

The package consists of a bare-bones implementation of the
"All-Pairs-Binary" algorithm described in the following paper:

R. J. Bayardo, Yiming Ma, Ramakrishnan Srikant. Scaling Up All-Pairs
Similarity Search. In Proc. of the 16th Int'l Conf. on World Wide Web,
131-140, 2007. (download from: http://www.bayardo.org/ps/www2007.pdf)

  * Click on the "Source" tab for instructions on downloading the source code. Makefiles are provided for both GNU g++ and Microsoft VC++ compilers.

  * Click on the "Downloads" tab to download a sample dataset to test your binary.


---


On Linux type systems with GNU g++, here's a quick sequence of commands to get up and running:

```
[~/ap-demo]: svn checkout http://google-all-pairs-similarity-search.googlecode.com/svn/trunk/ google-all-pairs-similarity-search-read-only
...
Checked out revision 26.
[~/ap-demo]: svn checkout http://sparsehash.googlecode.com/svn/trunk/ sparsehash-read-only
...
Checked out revision 46.
[~/ap-demo]: cd sparsehash-read-only/
[~/ap-demo/sparsehash-read-only]: ./configure
...
[~/ap-demo/sparsehash-read-only]: make
...
[~/ap-demo/sparsehash-read-only]: cd ../google-all-pairs-similarity-search-read-only/
[~/ap-demo/google-all-pairs-similarity-search-read-only]: make
...
g++ -DNDEBUG -I../sparsehash-read-only/src -O3 -D_FILE_OFFSET_BITS=64  -o ap main.o allpairs.o data-source-iterator.o
[~/ap-demo/google-all-pairs-similarity-search-read-only]: wget http://google-all-pairs-similarity-search.googlecode.com/files/dblp_le_fixed.bin.gz
...
10:20:59 (4.91 MB/s) - 'dblp_le_fixed.bin.gz' saved [26061298/26061298]
[~/ap-demo/google-all-pairs-similarity-search-read-only]: gunzip dblp_le_fixed.bin.gz
[~/ap-demo/google-all-pairs-similarity-search-read-only]: ./ap .9 dblp_le_fixed.bin > /dev/null
; User specified similarity threshold: 0.9
; Found 34807 similar pairs.
; Candidates considered: 4988117
; Vector intersections performed: 1618864
; Total running time: 5 seconds

```


---


To get going using Windows command shell, with Microsoft Visual C++ V9, svn.exe, wget.exe, and gunzip.exe:

```
C:\ap-demo>svn checkout http://google-all-pairs-similarity-search.googlecode.com/svn/trunk/ google-all-pairs-similarity-search-read-only
...

C:\ap-demo>cd google-all-pairs-similarity-search-read-only/

C:\ap-demo\google-all-pairs-similarity-search-read-only>"%VS90COMNTOOLS%vsvars32.bat"
Setting environment for using Microsoft Visual Studio 2008 x86 tools.

C:\ap-demo\google-all-pairs-similarity-search-read-only>nmake -f Makefile.w32 
...
/out:ap.exe 
...

C:\ap-demo\google-all-pairs-similarity-search-read-only>wget http://google-all-pairs-similarity-search.googlecode.com/files/dblp_le_fixed.bin.gz
...
15:20:55 (152.99 KB/s) - 'dblp_le_fixed.bin.gz' saved [26061298/26061298]

C:\ap-demo\google-all-pairs-similarity-search-read-only>gunzip dblp_le_fixed.bin.gz 

C:\ap-demo\google-all-pairs-similarity-search-read-only>ap.exe .9 dblp_le_fixed.bin > tmp.out
; User specified similarity threshold: 0.9
; Found 34807 similar pairs.
; Candidates considered:  4988117
; Vector intersections performed: 1618864
; Total running time: 9 seconds

```

