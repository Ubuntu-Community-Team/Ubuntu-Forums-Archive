---
title: "nVidia glx driver broken - can't uninstall..."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2007-11-20
so...  upgraded from feisty to gutsy...

had nvidia drivers installed with Envy.  Uninstalled drivers through envy prior to upgrade avoid this issue - to no avail.  Envy is unable to install the new drivers on the new kernel...  Synaptic see the nvidia-glx package as needing to be removed, but give me an error.  I read some posts tried:

sudo aptitude remove --purge nvidia-*  

it kicks this out:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "nvidia-*".  However, the following
packages contain "nvidia-*" in their name:
  nvidia-kernel-100.14.11 nvidia-legacy-kernel-source nvidia-glx-dev 
  nvidia-kernel-2.6.17-11-generic nvidia-settings nvidia-new-kernel-source 
  nvidia-glx-new nvidia-kernel-common nvidia-kernel-1.0.7184 
  nvidia-glx-legacy-dev nvidia-kernel-1.0.8774 nvidia-kernel-1.0.8776 
  nvidia-glx-new-dev nvidia-kernel-1.0.9631 nvidia-xconfig 
  nvidia-kernel-1.0.9755 nvidia-glx-legacy nvidia-kernel-source nvidia-glx 
The following packages have been automatically kept back:
  mplayer nfs-common 
The following packages have been kept back:
  nfs-kernel-server 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/4493kB of archives. After unpacking 0B will be used.
Selecting previously deselected package nvidia-glx.
(Reading database ... 113444 files and directories currently installed.)
Preparing to replace nvidia-glx 1:1.0.9631+2.6.20.6-16.30 (using .../nvidia-glx_1%3a1.0.9631+2.6.20.6-16.30_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up libexpat1-dev (1.95.8-3.4build1) ...
/usr/share/doc-base/expat: cannot open control file for reading: No such file or directory
dpkg: error processing libexpat1-dev (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libfontconfig1-dev:
 libfontconfig1-dev depends on libexpat1-dev; however:
  Package libexpat1-dev is not configured yet.
dpkg: error processing libfontconfig1-dev (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-glx (1.0.9631+2.6.20.6-16.30) ...

[COLOR="Lime"]Errors were encountered while processing:
 libexpat1-dev
 libfontconfig1-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libexpat1-dev (1.95.8-3.4build1) ...
/usr/share/doc-base/expat: cannot open control file for reading: No such file or directory
dpkg: error processing libexpat1-dev (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libfontconfig1-dev:
 libfontconfig1-dev depends on libexpat1-dev; however:
  Package libexpat1-dev is not configured yet.
dpkg: error processing libfontconfig1-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libexpat1-dev
 libfontconfig1-dev
[/COLOR]

This seems to be what synaptice is encountering...

How do I fix this???  

I just want to nuke whatever is choking and install the nVidia drivers, as I play Guild Wars though Ubuntu and need the card fully functional!!

TY

---

### Post by coolguy2006delhi on 2007-11-21
Just type 

$ sudo apt-get -f install 

before issuing your command. I think this will solve your problem.

---

