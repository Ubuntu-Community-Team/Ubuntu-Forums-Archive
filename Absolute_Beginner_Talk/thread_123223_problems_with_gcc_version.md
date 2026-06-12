---
title: "problems with gcc version"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by AUROBINDO MAJUMDAR on 2006-01-29
Hi !
I am quite new to Linux and  I have no programming skills. I have been using Fedora Core 2 for my office work for past one year (--mainly using OpenOffice for typing and spreadsheets). After a few failed attempts, I just about managed to install Breezy on my home PC:-D . For quite sometime, I have been wanting removeWindows from my home PC , but I am forced to keep a dual boot system, as Linux cannot handle my internal PCTel modem. I downloaded  a free driver for the modem, but compilation from source failed as the installed kernel seems to have been compiled with gcc-3.4 while gcc-4.0.2 has been installed on the system. I have been advised to either rebuild the kernel OR  downgrade gcc. 
With my skill level, rebuilding the kernel is not an option. I tried to first remove gcc-4.0.2 using Synaptic, but I had to cancel the operation on getting a warning to the effect that my system would be rendered unusable. Next, I installed gcc-3.3 through Synaptic, but the installed version of gcc remains 4.0.2.:???: 
I need lots of help from the Ubuntu community! Of course the easiest option may be to throw away the winmodem and get a proper Linux compatible modem. But I am not in a mood to spend anything on new hardware.;)

---

### Post by MartinG on 2006-01-29
You don't need to remove gcc-4.02, the system can have two versions side-by-side as long as you tell it which to use if you're not using the latest.

So install gcc-3.4 which is what you need for kernel-related compiles in Breezy, and then just before you start off with ./configure, do the following: export CC=gcc-3.4

---

