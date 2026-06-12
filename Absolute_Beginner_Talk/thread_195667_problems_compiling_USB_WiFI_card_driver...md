---
title: "problems compiling USB WiFI card driver.."
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Neurot1k on 2006-06-13
hey, I'm pretty new to Linux/Ubuntu, and I've been reading the HOWTOs for just about everything, but I pretty much need an internet connection to do anything that I want to do.
"ZyDAS IEEE 802.11 b+g Wireless LAN" is what it installs under on Windows.  The brand name on the box is Zonet.  Anyway, it came with a CD to install the driver, and it has the driver for windows, linux, and mac.  the linux driver came with a 12-page PDF on how to compile the thing, and i keep getting stuck somewhere around what would be step 5, it tells me

**3.2 Open the network interface:**
In our driver, we will stop all the commands until the network interface assigned to us is opened. One can open the network interface by the following command
]$ ifconfig ethX up
or
]$ ifconfig ethX <IP address>

but i've tried typing the first option, along with using sudo in front of it, and about 5 other combinations of things, and i always get an error.

does anyone know what's going wrong?  i attached the .tar.gz file to this (and the pdf can be downloaded at [http://www.filefactory.com/?0dcdbf)](http://www.filefactory.com/?0dcdbf)), so if someone wants to download them and compile it and tell me what i'm doin wrong, they can.  i dont know, i'm just pretty lost and pretty new to linux.

---

### Post by shof2k on 2006-06-13
Have a read of my how to at [http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259).  You can use whichever zydas driver will work with your computer.

Hope that helps,

---

### Post by Neurot1k on 2006-06-13
yeah, i'm not sure how it works with 6.06... but I actually have to be connected to access things on the internet...?  i had a problem almost right away with that HOWTO..

right after the "sudo apt-get remove wpasupplicant" line, it returned

```
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package wpasupplicant
```

but i just continued on with your instructions.. and this is what happened next;
```
crux@ubuntu:~$ sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package kernel-package
```

so i decided to quit there before anything else could go wrong.

---

### Post by shof2k on 2006-06-14
You could use a LAN cable connection for the interim then go to wireless once it all works. 

How do you write your posts?  If you have a windows partition or another computer, use that to obtain the packages required.

---

