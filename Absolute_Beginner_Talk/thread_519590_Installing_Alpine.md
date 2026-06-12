---
title: "Installing Alpine"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Jeeevs2001 on 2007-08-07
Hello all, 

I am having a small problem trying to install Alpine on Ubuntu. I have downloaded the latest .deb and when I attempt to install with sudo dpkg --install, i get the following error: 

 dpkg-divert: `diversion of /usr/bin/pico to /usr/bin/clone-editor-moved by alpine' clashes with `diversion of /usr/bin/pico to /usr/bin/clone-editor-moved by pine'
dpkg: error processing alpine_0.999_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:

Unfortunately I have no idea what this means or how to resolve it! Any help would be appreciated.

Thanks in advance.

---

### Post by vikram on 2007-08-07
its much simple if you use apt-get or adept or synaptic to install Alpine rather than trying to install .deb files. The coolest feature of Kubuntu (and Ubuntu) IMO is the easy of installation. Unless a software is not available in the repos I would recommend adept or synaptic if you prefer GUI or
apt-get if you prefer CLI

---

### Post by Jeeevs2001 on 2007-08-09
Hi, 

I agree that would be the simplest way however,  I have tried using 'apt-get install' but the package is not available (I am running Ubuntu 6.06 Server). I understand it is available in the Feisty repositories but the version is not up to date, and I have no idea how to add the Feisty repositories! 

Thanks for your advice though.

---

