---
title: "freebasic"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by djthain on 2006-04-25
I have installed Freebasic on Ubuntu but I get this error when trying to create the executable file.

root@ubuntu:/arclib# fbc ck004.bas
/usr/share/freebasic/bin/linux/ld: cannot find -lc
root@ubuntu:/arclib#

What is needed to make this work?

djthain

---

### Post by sir_mud on 2006-08-06
do you have the build-essential package installed? 
"sudo apt-get install build-essential"
also, make sure you have all the -dev versions of the libraries you're using

---

