---
title: "MD5 Checksum"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by thehandyman on 2007-12-08
Hey all, I am new to Linux and have no earthly idea what or where the MD5 checksum is or how to use, HELP please. Nero is telling me that my bock size does not match when I try to burn the iso. Also the file size does not match what I was supposed to download.:confused:

---

### Post by aysiu on 2007-12-08
> **thehandyman said:**
> Hey all, I am new to Linux and have no earthly idea what or where the MD5 checksum is or how to use, HELP please. Nero is telling me that my bock size does not match when I try to burn the iso. Also the file size does not match what I was supposed to download.:confused:
This should help:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by CouchMaster on 2007-12-08
MD5 checksum is an algorithm used to calculate a number based on the size of a file.
You can download free MD5 calculators (Nero won't do it but K3B will) from the web to calculate the ISO you downloaded and compare it to what the website says it's supposed to be.
If they match you have a good download - if not you need to re-download.
Google MD5...

---

### Post by Harpoon on 2007-12-08
What it is:  a "hash" routine that calculates a string of numbers/letters that represents the contents of a file (basic non-tech answer).  It is used to verify a file's integrity--when I post a file and the md5 checksum, you can calculate the checksum for the file you downloaded to be sure you got it all without errors, and no one has messed with it.

Where, how:  in a terminal just type md5sum and then the name of the file you want to check.  Compare the number printed on the screen with the one provided  by the source.,

You can get better/more detailed explanations googling around for this, or tiger tree hash or sha1 (all different methods for doing the same thing),.

Basic help can be gottten with thyping md5sum --help (or -h) I always forget which.

BTW, if the checksums don't match, you may have a bad download.

Hope that answers parrt of your questions.  As to the blocksize error, can someone address that one directly?

---

### Post by laidback on 2007-12-08
You can get Ubuntu to calculate an md5sum....in a terminal type md5sum -help for info.

To use:-

$ md5sum </path/filename>

---

