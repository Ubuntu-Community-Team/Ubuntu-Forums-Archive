---
title: "Virtualbox and kernel ?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-03
Okay, so after several attempts, I managed to install Virtualbox on Feisty Fawn. However, it gave me some message about some kernel issue, something about not finding kernel? 

I've spent almost 2 hours looking up on issues related to Virtualbox, already, so some help would be appreciated. I actually read the user manual about the kernel but I still have no idea where to get the kernel from or how to install it.

From vbox-install.log , it says to run some commands on kernel src but how? 
 
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\ 

Command line input from trying to setup kernel again:
hidan@lucifiel:~$ sudo /etc/init.d/vboxdrv setup
Password:
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
hidan@lucifiel:~$

---

### Post by Lucifiel on 2007-05-03
From this page, I gathered the following instructions, however, I can't even find the kernel image or source or whatever for 2.6.20-15 :
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

hidan@lucifiel:~$ uname -r
2.6.20-15-generic

#  snauth Says:
January 23rd, 2007 at 8:26 am

I would try this:
Find out your kernel version with
uname -r
Download the sources from [http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/)
Unpack the sources wherever you want them:
tar xvjf linux-2.x.x.x.tar.bz2
Set the environment variable KERN_DIR:
export KERN_DIR="/path/to/kernelsource"
In the same terminal session try to reinstall VirtualBox.
Good luck!

---

### Post by Lucifiel on 2007-05-04
Oh, I finally managed to fix this but I'm not sure what did.

What I did was install all the related dependencies and reinstall Virtualbox a few times. Then, ran the following command to give permission to my vboxdrv because somehow, all the other commands weren't working.

 sudo chmod a+rw /dev/vboxdrv

Although, now I'm trying to find out how to test my Partimage clone of my Ubuntu installation, with Virtualbox. I actually tried booting with Systemrescuecd so I could run Partimage and restore from /dev/hdc2 but then realised that doh... that wouldn't quite work. :/

---

### Post by nanocosm on 2007-05-07
```
sudo dpkg-reconfigure dash
```

It wil ask you wether you want to use Dash instead of Bash, say no then try again.

---

