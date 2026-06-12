---
title: "dial-up catch 22"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Justus on 2005-12-07
So here's my problem: I am unable to connect to Dial-up using Ubuntu and my internal Conexant modem, and all the solutions I've tried involve having to compile things with the make command, which I can't do, because make isn't installed, and I can't install it, because I can't connect. Is there anyway to download the package that contains "make" on Windows and then transfer it to Linux and install it? Or any solutions that don't involve compiling source code? Thanks everyone

EDIT: I'd also be very greatful if people who have been able to connect with a Conexant modem could post here (or even people who are still trying). Thanks!

Note: I accidently posted this first in the "Desktop support" or whatever forum. Sorry about that, it's supposed to be here.

---

### Post by cosmin1086 on 2005-12-08
The make package is avaiable on the install cd. You can just search for this package in Synaptic. If you don't have the install CD, go to [http://packages.ubuntu.com](http://packages.ubuntu.com), and search for the 'make' package there. You can download it onto your windows partition, and then access it from Ubuntu.

For the .deb files, it's actually quite easy:
cd /home/YOU/dir_where_you_saved_file
sudo dpkg -i filename.deb

--hope this helps

---

