---
title: "fujitsu fdx310"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by rabbiedoo on 2006-01-16
I have installed the most recent Breezy release and need to get an internet connection.  I have downloaded (via Windows) a tar file with drivers for my Fujitsu FDX310 USB modem connecting to a Dell Dimension 2400 (Intel). It is known to work with Suse and Mandrake, don't know about Ubuntu. The files are unzipped in my home directory but how exactly do I intall them. The instructions say type 'make' and then 'make install' but these are not recognised in sudo bash.  Will dpkg work in sudo, and if so, what do I type. 

Alternatively how do I use the much vaunted Synaptic to find the files on the home directory and then install. It appears to only be able to search the internet.:confused:

---

### Post by Sef on 2006-01-17
> The instructions say type 'make' and then 'make install' but these are not recognised in sudo bash.

Did install build-essential?  If not, you will get that error.

Terminal: sudo apt-get install build-essential

---

