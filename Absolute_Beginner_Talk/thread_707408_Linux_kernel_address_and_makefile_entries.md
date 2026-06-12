---
title: "Linux kernel address and makefile entries"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Midgetprawn on 2008-02-25
Still Green and cabbage looking 
I have downloaded slmodem-2.9.9 as a tarball and I have unpacked it and follwed the instructions so far but before I can 'make' the file it asks for the directory route for the linux kernel to be written into the makefile .
I am running Gutsy Gibbon with kernel 2.6.22-14
Any suggestions on the correct entry in makefile as I keep getting errors.
PS I am installing modem packages so that I can use the modem to access the internet to download any packages.......

---

### Post by Cypher on 2008-02-25
Check in /usr/src and you should find a linux-headers-2.6.22-14 directory, you can point your makefile to that as that's the Kernel headers, if that doens't work, then you'll have to download the Kernel sources with
```

sudo apt-get install linux-source-2.6.22

```
This will place linux-source-2.6.22.tar.bz2 in /usr/src, uncompress it there with
```

cd /usr/src
sudo tar -jxf linux-source-2.6.22.tar.bz2

```
Now point your makefile to /usr/src/linux-2.6.22

---

