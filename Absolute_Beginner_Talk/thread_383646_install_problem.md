---
title: "install problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by bry2o on 2007-03-13
I just installed Ubuntu 6.1 and was trying to install some programs, but I am getting this problem which isn't letting me install. For example, I was trying to install emacs, but when I type the command: "sudo apt-get install emacs" I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacs21 emacs21-bin-common emacs21-common emacsen-common liblockfile1
  libungif4g xaw3dg
Suggested packages:
  emacs21-el
The following NEW packages will be installed:
  emacs emacs21 emacs21-bin-common emacs21-common emacsen-common liblockfile1
  libungif4g xaw3dg
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I don't know what it means by "Unable to lock the download directory." If anybody could help me out, I'd greatly appreciate it.

---

### Post by dstew on 2007-03-13
The download directory might be in use by another process, like a file viewer. Close other programs and windows before trying apt-get again.

---

### Post by haricharan on 2007-03-13
make sure u dont have ur synaptic or package manager open while doing installation in terminal....

---

### Post by wpshooter on 2007-03-13
Make sure you have ALL repositories checked in Update Manager (including universe and multi-universe) and then look for and install this program thru Synaptic.

Good luck.

---

### Post by bry2o on 2007-03-13
><' Thanks a lot it works now. Time to go learn more about linux.

---

