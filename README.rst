Fortran 2003 interface to dSFMT
===============================

A Fortran 2003 interface to dSFMT (double precision SIMD-oriented Fast Mersenne
Twister) pseudo-random number generator.

dSFMT was written by Mutsuo Saito and Makoto Matsumoto (Hiroshima University).
This Fortran 2003 interface was written by James Spencer (Imperial College London).

Both dSFMT and dSFMT_F03_interface are released under the new/modifed BSD
license.  See LICENSE.txt in the source subdirectories for more details.

Directory contents
------------------

dSFMT-src-2.2.3/
    Original dSFMT (v2.2.3) implementation in C; taken from
    http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/SFMT/.
    Also contains functions to convert the dSFMT state to/from strings by Andrea Mennucci
    (see http://mennucc1.debian.net/dSFMT_src_state/)
dSFMT_F03_interface/
    Fortran 2003 interface (with help of a small amount of C code for memory
    allocation and deallocation). 
test/
    Run make to compile and run simple tests to ensure the Fortran and
    C interfaces produce identical streams of pseudo-random numbers.

Documentation
-------------

Please see the dSFMT documentation (dSFMT-src-2.2.3/html) and comments in the
dSFMT_interface module.

Compilation
-----------

I recommend simply copying the relevant files to a subdirectory and directly
compiling them as part of a larger project rather than compiling and linking to
a library.  The following files are required::

    dSFMT-src-2.2.3/dSFMT.c
    dSFMT-src-2.2.3/dSFMT_str_state.c
    dSFMT-src-2.2.3/dSFMT*.h
    dSFMT-src-2.2.3/LICENSE.txt
    dSFMT_F03_interface/dSFMT_interface.F90
    dSFMT_F03_interface/dSFMT_utils.c
    dSFMT_F03_interface/LICENSE.txt

.. IMPORTANT::

    To obtain the best performance it is vital to define the HAVE_SSE2
    C pre-processing macro on processors which have SSE2 instructions.

    Substantial (ie 25%) speedups can be achieved with some compilers by using
    interprocedural optimization (i.e. -ipo for Intel compilers and -flto for
    GCC compilers).
