---
title: "what is this i havent found anything about it in the wiki"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-03-18
i was looking about for my driver and found this i have been trying ndiswrapper for days and now i found this does this mean that i have a native driver somewhere on my computer or something

Additional Installation Notes for Various Linux Distributions
Broadcom BCM4400 Linux Driver
Version 3.0.7
10/31/2003

Broadcom Corporation
16215 Alton Parkway,
Irvine, CA 92619-7013

Copyright (c) 2000-2003 Broadcom Corporation
All rights reserved


Table of Contents
=================

Introduction
Limitations
Prerequisites
Prepare Kernel Source Tree (United Linux 1.0 Distributions)


Introduction
============

This file contains additional installation notes for the Broadcom bcm4400
Linux driver that are specific to certain Linux distributions. General
installation notes are contained in README.TXT.


Limitations
===========

The current version of the driver has been tested on the following Linux
distributions:

Distributions for i386:

Red Hat 8.0, 9.0 and 2.1AS
UnitedLinux 1.0 based distributions (UnitedLinux 1.0, SuSE SLES8, 8.1,
and SCO 4.0)
UnitedLinux 1.0 SP1
Mandrake 9.0


Prerequisites
=============

In order to compile your Broadcom Linux driver, you must first
have a properly compiled kernel source tree which matches your running
kernel. You must also have a working C/C++ compiler and all the associated
dependencies installed before attempting to compile the driver.

On Red Hat distributions, if you have opted for a custom installation, you
need to select "Development Tools" and "Kernel Development" to install
the necessary tools and kernel source tree.

On United Linux based distributions, you must change the software packages
installed by default when presented with the Installation Settings. Under
software selelction, select "Detailed Selection". In this area ensure that
"C/C++ Compiler and Tools" is selected. This should install the C/C++
compiler as well as the kernel-source files.

For further assistance, please review your Linux documentation.


Prepare Kernel Source Tree (United Linux 1.0 Distributions)
================================================== =========

The following instructions pertain only to United Linux 1.0 based
distributions (SuSE SLES8, SuSE 8.x, SCO4.0, etc.) These steps are not
needed for Red Hat, Mandrake and other similar distributions.

1. Prepare the kernel source tree. These steps are necessary in order to
compile a driver that will match your running kernel.

cd /usr/src/linux-<kernel_version>.SuSE
cp /boot/vmlinuz.config .config
cp /boot/vmlinuz.version.h include/linux/version.h
cp /boot/vmlinuz.autoconf.h include/linux/autoconf.h
make oldconfig
make dep

2. Now build and install the Broadcom Linux driver using either the rpm or
tar archive installation files. The procedures are found in README.TXT.

---

### Post by katarot on 2006-03-18
how do i do this im really confused 
This procedure requires you to have first compiled and rebooted on a new kernel
im really stuck here

---

### Post by Pragmatist on 2006-03-18
According to this, you need some more packages:
[http://packages.ubuntulinux.org/warty/net/bcm4400-source](http://packages.ubuntulinux.org/warty/net/bcm4400-source)

You can get them in synaptic, just type:
```
sudo synaptic
```
then use the search feature with these keywords (one at a time, of course)
[B]bcm4400-source
kernel-package
dpkg-dev
debhelper (>=4)
debconf-utils
module-assistant[/B]

Install all of these packages.  The advice on the above link is:
> This package provides the source code for the bcm4400 module provided by Broadcom. You will need make-kpkg from kernel-package to be able to compile modules usable with a Debian kernel.

Note that the Linux kernel >= 2.4.22 includes the Broadcom 4400 driver. You may want to consider using the kernel driver instead. 

Synaptic's description has a little more information:
> Note that the Linux kernel >= 2.4.22 includes the Broadcom 4400 driver. You
may want to consider using the kernel driver, named 'b44', instead.

So you probably could try this if you wanted:
```
sudo modprobe b44
```

---

### Post by katarot on 2006-03-18
it didnt work it is this laptop   argghh  it hates me
i swear i have tried everthing and it is correct 
ndiswrapper 
1st attempt
downloaded the file of dell
extreacted it to usb flash moved .sys and .inf to desktop on ubuntu
go to terminal and type

sudo apt-get install ndiswrapper-utils
cd (location of windows drivers)
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo ifup wlan0
ignoring unknown interface wlan0 = wlan0

sudo ndiswrapper -l
bcmwl5 hardware present driver present
after that i went to system > administration > networks
and wlan0 was not listed

attempt 2
to remove failed attemps

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

to get the card working

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

sudo ifup wlan0
ignoring unknown interface wlan0 = wlan0

sudo ndiswrapper -l
bcmwl5 hardware present driver present

again i go to system > administration > networks
and wlan0 was not listed

martin@martin:~$ iwconfig -a
-a No such device

martin@martin:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

martin@martin:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:14:22:8E:B7:91
inet addr:192.168.2.2 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::214:22ff:fe8e:b791/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1747 errors:0 dropped:0 overruns:0 frame:0
TX packets:1747 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:156677 (153.0 KiB) TX bytes:156677 (153.0 KiB)

sit0 Link encap:IPv6-in-IPv4
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

martin@martin:~$


and i also tried all that with sudo -s 

then i try to do it with a native driver and it still dosent work 
why why why why 

there must be someway

---

### Post by Pragmatist on 2006-03-18
Did you do anything that I suggested in my previous post?

---

### Post by katarot on 2006-03-18
yeah apparently it is invalid directory and when i try to move it i dont have permission im screwed really iam im going to die

---

### Post by Pragmatist on 2006-03-18
> yeah apparently it is invalid directory and when i try to move it i dont have permission im screwed really iam im going to die

This kind of comment doesn't help.  We are happy to help you, but you have to be specific and give us the information we need. Now....

1.) What is an invalid directory?  Please cut/paste the content of your terminal and post here.

2.) What **exactly** did you try from my earlier suggestions?

---

### Post by katarot on 2006-03-18
sorry 
i cant i have to use xp to access the internet
emm i could do what i did earlier and put it on disk 
ok i do that i might take a while tho

---

### Post by Pragmatist on 2006-03-18
Ok a couple of things:
1.) The approach you were using before wasn't for Ubuntu/Debian So it isn't too surprising that it didn't work! :)
> Limitations
===========
The current version of the driver has been tested on the following Linux
distributions:

Distributions for i386:

Red Hat 8.0, 9.0 and 2.1AS
UnitedLinux 1.0 based distributions (UnitedLinux 1.0, SuSE SLES8, 8.1, and SCO 4.0)
UnitedLinux 1.0 SP1
Mandrake 9.0]

2.) Since you don't have an internet connection, first try following these directions:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Once you have an /etc/apt/sources.list file, uncomment the line that looks like this:
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

by taking away the hash mark (#) so it looks like this now:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

You could also use this site to download the list of packages I gave in an earlier post:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

However, then you would have to burn them to a CD or otherwise get them to linux.

---

