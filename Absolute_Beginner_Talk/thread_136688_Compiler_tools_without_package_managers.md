---
title: "Compiler tools without package managers"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by Jabithew on 2006-02-26
I've added ubuntu 5.10 to my laptop. THis machine has only a wireless connection. Other users have reported success in using ndiswrapper and the native windows driver on my chipset (BCM4306).

However, to install ndiswrapper I need to compile it from source. This is not such a problem, except I have no compiler. For obvious reasons I cannot get driect access to the internet, for less obvious reasons I don't have the install cd handy either, so
```
sudo apt-get install build-essential
```
doesn't work. 

However, I can transfer .deb files from the net using my usb disk. I have treid that with gcc and all dependant packages, which I copied to my desktop and then installed using 
```
cd Desktop
sudo dpkg -i gcc.deb
```
(I renamed the files to save time.)
However, I find that i have no 'make' command and also typing 
```
gcc --version
```
into the terminal does nothing. Help?

---

### Post by stuporglue on 2006-02-26
> However, to install ndiswrapper I need to compile it from source.

There are packages for ndiswrapper for Ubuntu. The deb apt wanted to download for me is named "ndiswrapper-utils_1.1-4ubuntu2_i386.deb. Here's a link to it...

[http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb)

---

### Post by curtis on 2006-02-26
Actually I found that 1.1 did not work with BCM4306.
Do a apt-cache showpkg build-essential (Then note all packages it reverse-depends and manually download them)

---

### Post by az on 2006-02-26
[QUOTE=curtis]Actually I found that 1.1 did not work with BCM4306.
Do a apt-cache showpkg build-essential (Then note all packages it reverse-depends and manually download them)[/QUOTE]

ndiswrapper-utils is on the cd.

You need the most recent .inf file for your wireless card, not the most recent ndiswrapper version AFAIK.  The one in breezy should work fine.  If you check the ndiswrapper changelogs, there is no mention of broadcom chipsets after the version of ndiswrapper previous to breezy's.

---

