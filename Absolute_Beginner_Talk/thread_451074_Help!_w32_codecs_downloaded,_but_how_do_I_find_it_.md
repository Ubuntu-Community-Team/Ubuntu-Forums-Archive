---
title: "Help! w32 codecs downloaded, but how do I find it to install it?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-21
I followed the instructions for downloading the w32 codecs from medibuntu using terminal, but now that the download has completed, I do not know how to find the downloaded package in my computer, and how to install it. Here below is the printout from the download process in terminal. Please help!

swarup@swarup-laptop:~$ wget [http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
--21:28:33--  [http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
           => `w32codecs_20061022-0medibuntu1+build1_i386.deb'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,254,076 (14M) [application/x-debian-package]

84% [==============================>      ] 11,992,336    --.--K/s    ETA 19:40^100%[====================================>] 14,254,076    10.90K/s    ETA 00:00

23:33:25 (1.86 KB/s) - `w32codecs_20061022-0medibuntu1+build1_i386.deb' saved [14254076/14254076]

swarup@swarup-laptop:~$ sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

---

### Post by Bachstelze on 2007-05-21
The package is in your home directory, since you were in it when you ran wget. You don't need ro worry about it though, the dpkg command installed it.

---

### Post by swarup on 2007-05-21
It's ok, never mind.....I found the package in my my home folder, and right clicked on it. It offered to unpack and install it..............but then told me I already have a later version of this very thing already installed in the computer. Thanks anyway!

---

