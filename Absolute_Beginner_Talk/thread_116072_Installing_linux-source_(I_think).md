---
title: "Installing linux-source (I think)"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by Jim Smith on 2006-01-11
I've been toying with Ubuntu for a few days now, mostly trying to get my sound card and NIC to work with it.  In both cases, I've run into a wall where I'm told to use the linux-source package in the /usr/src/linux directory, which doesn't seem to exist.  As best I can tell I'm supposed to download linux-source off the internet with apt-get.  But that puts me in a Catch-22: I can't get the NIC working without linux-source which I can't get until my NIC works.

I have a feeling this is something really really obvious, but my brain is fried just getting this far.

---

### Post by Masteroc on 2006-01-11
do you have another linux machine that you can download the source on?

You might even be able to download it onto a windows machine and then burn it to cd.

---

### Post by az on 2006-01-11
[QUOTE=Jim Smith]I've been toying with Ubuntu for a few days now, mostly trying to get my sound card and NIC to work with it.  In both cases, I've run into a wall where I'm told to use the linux-source package in the /usr/src/linux directory, which doesn't seem to exist.  
...

I have a feeling this is something really really obvious, but my brain is fried just getting this far.[/QUOTE]


You need the linux-headers package.  You also need build-essential.  All of those are on the install cd and most probably cahced on your harddrive.  Just install them with synaptic.

The catch-22 is the oversight that the kernel was not built with the same compiler as the rest of the distribution.  You need to fetch gcc-3.4 (which depends on gcc-3.4-common and cpp-3.4)  Those three packages are *not* on the cd.  Apparently, this will not happen again.


You do not need the ful source, just the headers.  They are already comfigured for your running kernel (install the version that matches your kernel, the  368 one.

---

### Post by Jim Smith on 2006-01-11
[QUOTE=azz]You need the linux-headers package.  You also need build-essential.  All of those are on the install cd and most probably cahced on your harddrive.  Just install them with synaptic.

The catch-22 is the oversight that the kernel was not built with the same compiler as the rest of the distribution.  You need to fetch gcc-3.4 (which depends on gcc-3.4-common and cpp-3.4)  Those three packages are *not* on the cd.  Apparently, this will not happen again.[/QUOTE]

I've already installed gcc-4.0 and build-essential with Synaptic.  The closest I could find to a linux-headers package was linux-headers-2.6.12-9 and linux-headers-2.6.12-9-386, both of which I installed.

I may be asking the wrong question, though.  I'm trying to install tulip.o so I can use my old Linksys NIC.  The instructions I've found tell me to compile tulip.c by entering the command

gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/net/inet -Wall -Wstrict-prototypes -O6 -c tulip.c `[-f/usr/include/linux/modversions.h] && echo -DMODVERSIONS`

Since there is no /usr/src/linux directory and there is no /usr/include/linux/modversions.h on my system, the compilation fails and I get several hundred errors.  I'd rewrite the gcc command to reflect the correct paths, but I don't know what those are supposed to be.  Changing /usr/src/linux to /usr/src/linux-headers-2.6.12-9-386 or /usr/src/linux-headers-2.6.12-9 didn't help.

---

