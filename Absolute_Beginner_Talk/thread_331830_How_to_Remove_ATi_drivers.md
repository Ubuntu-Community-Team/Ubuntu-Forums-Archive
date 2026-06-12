---
title: "How to Remove ATi drivers?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-01-05
Ok, i've been searching around for info about removing ati binary drivers but i can only find guides to install them. ATM i ran the "dpkg-reconfigure -phigh xserver-xorg" command in the recovery terminal. X starts up ok, but the ati drivers are still in there and the ATi control panel. When i try to remove them from Add/Remove, i get an error saying that the ATi drivers cannot be installed on my computer, even though i'm trying to remove them...

Any ideas?

oh i forgot to mention, i just upgraded with a new nvidia card which is why i'm trying to get rid of the ati drivers...

---

### Post by M_the_C on 2007-01-05
How did you install the drivers?

Did you type something like sudo apt-get(or aptitude) install ati-***?

if so just type remove instead of install.

---

### Post by Muppeteer on 2007-01-05
Well i followed this guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

So there's really no "sudo apt-get remove" command i can use.

When i try installing the nvidia drivers using this command 
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```

I get the following error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
(Reading database ... 116534 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It looks like the fglrx driver is still installed and conflicting with the nvidia driver. I did already run a command to remove the fglrx driver 
```
sudo apt-get install xorg-driver-fglrx
```

So i don't know what else to do ](*,)

---

### Post by M_the_C on 2007-01-05
I found [this]("http://www.ubuntuforums.org/showthread.php?t=222083&highlight=dpkg-divert%3A+%60diversion+of+%2Fusr%2Flib%2FlibGL.so.1+to+%2Fusr%2Flib%2Fnvidia%2FlibGL.so.1.xlibmesa+by+nvidia-glx%27+clashes+with+%2Fusr%2Flib%2Ffglrx%2FlibGL.so.1.xlibmesa+xorg-driver-fglrx%27") thread which seems to solve your problem.

---

### Post by Muppeteer on 2007-01-05
Thanks mate, solved my problem :D

---

