---
title: "help compiling"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by kkellner on 2006-10-18
I am trying to learn to compile, and I have a question:

everytime I download a tar.bz2 I want to compile, I extract it, move into the direcotry and run ```
./configure
``` (which usually seems to work) and then I try to run 

```
make
``` but i always get an error that says "no target" or "makefile not found" even though I can see the makefile.am in the folder of the app I am trying to compile.  What step am I missing here?  Does the extracted folder need to be in a specific directory?

---

### Post by Malakia on 2006-10-18
Check to make sure that you have make installed, that is probably the source of your problem.

---

### Post by Sef on 2006-10-18
To compile, you need build-essential.  Have you installed it?

sudo apt-get update

sudo aptitude install build-essential

---

### Post by kkellner on 2006-10-18
thank you for responding.

yes both make and build-essential are installed and updated.  this is exactly what it says when I attempt to 'make' after './configure' :

make: *** No targets specified and no makefile found.  Stop.

this appears to happen with everything I try to compile, maybe I'm missing an obvious step because I am a beginner.

---

