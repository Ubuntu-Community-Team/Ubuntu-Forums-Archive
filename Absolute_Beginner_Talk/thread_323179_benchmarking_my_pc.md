---
title: "benchmarking my pc"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by magicsmoke on 2006-12-21
Not sure if this is the correct category to post this but...

Can anyone tell me how I can benchmark my Ubuntu system's performance?  I'm having difficulty finding some open-source software to do it for Linux.  I'm looking for how many GFlops/sec my PC can do or something along those guidelines.

---

### Post by magicsmoke on 2006-12-21
nothing?

---

### Post by az on 2006-12-21
There are some apps in the repositories for benchmarking disk I/O.

You can also time how long it takes for you to compile the kernel - that is what is considered a real-world benchmark.

You can also time how long it takes your box to do some math:
[http://ubuntuforums.org/showthread.php?t=60264&highlight=super+pi](http://ubuntuforums.org/showthread.php?t=60264&highlight=super+pi)

emma@ubuntu:~$ apt-cache search benchmark
bonnie++ - Hard drive bottleneck testing benchmark suite.
siege - Http regression testing and benchmarking utility
avifile-utils - utility programs using the avifile library
contest - The linux kernel responsiveness benchmark
cstream - general-purpose stream-handling tool similar to dd
dbench - The dbench (disk) and tbench (TCP) benchmarks
libamstd-ruby1.8 - AMbitious STanDard library for Ruby 1.8
libbenchmark-ocaml-dev - OCaml benchmarking library
libcrypto++-dev - General purpose cryptographic C++ library - development
libcrypto++-utils - General purpose cryptographic library - utilities and data files
muscle - [Biology] multiple alignment program of protein sequences
nhfsstone - NFS benchmark program
postal - SMTP benchmark - the mad postman.
postgresql-contrib-7.4 - additional facilities for PostgreSQL
postgresql-contrib-8.0 - additional facilities for PostgreSQL
postmark - File system benchmark from NetApp
scsitools - Collection of tools for SCSI hardware management
stress - A tool to impose load on and stress test a computer system
tiobench - Threaded I/O bench for Linux
xengine - A benchmark program for the X Window System.
iozone3 - Filesystem and Disk Benchmarking Tool
apache2-utils - utility programs for webservers
postgresql-contrib-8.1 - additional facilities for PostgreSQL


emma@ubuntu:~$ apt-cache show bonnie++
Package: bonnie++
Priority: optional
Section: utils
Installed-Size: 144
Maintainer: Russell Coker <russell@coker.com.au>
Architecture: i386
Version: 1.03abuild1
Replaces: zcav, bonnie
Provides: zcav, bonnie
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.0-7), libstdc++6 (>= 4.0.0-7)
Conflicts: zcav, bonnie
Filename: pool/main/b/bonnie++/bonnie++_1.03abuild1_i386.deb
Size: 41854
MD5sum: 9b0de03c9f65abeb4bbe50b32f83152c
Description: Hard drive bottleneck testing benchmark suite.
 It is called Bonnie++ because it was based on the Bonnie program.  This
 program also tests performance with creating large numbers of files.
 Now includes zcav raw-read test program.  A modern hard drive will have more
 sectors in the outer tracks because they are longer.  The hard drive will
 have a number (often more than 8) of zones where each zone has the same
 number of sectors (due to the need for an integral number of sectors per
 track).  This program allows you to determine the levels of performance
 provided by different zones and store them in a convenient format for gnuplot.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

emma@ubuntu:~$

---

### Post by magicsmoke on 2006-12-21
Thank you, that is very helpful.

---

### Post by ChadMMc on 2006-12-21
Hi, you can also get the  hardinfo application through the repositories...it had about 4-6 different benchmarks in it.

---

