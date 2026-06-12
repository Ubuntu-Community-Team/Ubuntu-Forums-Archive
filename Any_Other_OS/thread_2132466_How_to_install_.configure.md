---
title: "How to install ./configure"
date: 2013-04-04
forum: Any Other OS
---

### Post by afz12 on 2013-04-04
I am posting in Ubuntu although I have a problem using ./configure for *.bz2 files etc . Mint - this OS seems to be based on the same principles, perhaps and my hope is that someone will have a solution in either forum, or that there is none. For example I want to update quicktime in firefox but I can't get sudo aptitude install * to work in a terminal, although this worked for firefox. I downloaded the *.bz2 file but ./configure is not recognized. Is there a way to add this function?

---

### Post by lisati on 2013-04-04
Assuming there is a ./configure file present, you need to unzip the bz2 file to its own directory and navigate to the directory with the command line before trying to run ./configure from the command line.

Have a look fore a "readme" file in the bz2 archive: it should have the necessary information in it.

---

### Post by alphacrucis2 on 2013-04-04
If you want to compile stuff then make sure you install the build-essential package first.

---

### Post by Perfect Storm on 2013-04-05
Moved to Other OS/Distro Support.

---

### Post by oldos2er on 2013-04-05
Do you have a link to the bz2 file you downloaded?

---

### Post by mamamia88 on 2013-04-06
First and foremost you have to have everything required for the packages you are trying to compile first.   Secondly you need to unzip it and cd to the directory containing the ./configure file before running it.  Then hopefully it goes smoothly.   There is usually a readme file contained within that gives detailed instructions.

---

