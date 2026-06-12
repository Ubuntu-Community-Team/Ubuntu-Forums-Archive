---
title: "pkg mgr error"
date: 2011-05-18
forum: Apple Hardware Users
---

### Post by n4dhp on 2011-05-18
ubuntu 11.04

uname -a 
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

when performing following command:
sudo apt-get update
and also when opening synaptic package manager:  


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

the file reference exists.

ubuntu is installed within a VMWare virtual environment on MAC latest O/S

---

### Post by jerrrys on 2011-05-19
could it be a corrupted file name?

think i would rename that file  (i usually just put a 2 on the end of it). create a new file with your text editor with the original file name and see if it flies.

---

