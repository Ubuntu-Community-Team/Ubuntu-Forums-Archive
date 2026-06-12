---
title: "Two questions about kernel headers."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Mochtroid-X on 2007-01-16
My first question is where do I download the kernel headers? I usually stumble onto them eventually whenever I (re)install Ubuntu on a machine, but can never remember where I got them.

My second question is what are kernel headers and what do they do? I only know that I require them for my wireless usb... which I have not yet had the time to install... ](*,)

---

### Post by rai4shu2 on 2007-01-16
To install kernel headers type the following in a console:

sudo apt-get install linux-headers-386

Kernel headers provide information for building kernel modules from source, which is sometimes the only way drivers are provided.

---

### Post by az on 2007-01-16
> **rai4shu2 said:**
> To install kernel headers type the following in a console:

sudo apt-get install linux-headers-386
.

If you are not yet connected to the internet, you will find the linux headers in a repo on the install disk, apart from the live session.  Just boot into Ubuntu and then pop the cd into the drive.  The package manager should come up.

From the command line run

sudo apt-cdrom add

and then install the linux-headers package.  Linux-headers-386 is for Dapper.  For Edgy, use linux-headers-generic.

---

### Post by Mochtroid-X on 2007-01-16
If I download the kernel headers from the internet, does that also update my kernel to the latest version? Before I would just search for kernel in the synaptic package manager and download everything that came up...

---

### Post by mcduck on 2007-01-16
If you install package 'linux-generic' it will make sure that you will always have the latest kernel, headers and restricted modules available in the repositories. This is far smoother way of doing it than installing any specific version of the headers package.

If you did a clean install of Edgy that package should already be installed.

(for Dapper use linux-386, linux-686 or whatever kernel fits your CPU best)

---

### Post by SeanONe on 2007-02-08
I'm told by adept that I have 4 upgradable packages
linux-headers-386
linux-headers-generic
linux-image-386
linux-restricted-modules-386

They're all installed versions 2.6.17.10 and the candidates are all 2.6.17.11

When I request Upgrade, the requested field changes to "BREAK (Upgrade)" in a very dramatic red colour.

Erm, what's that?

---

### Post by az on 2007-02-08
You are not giving enough information.

Try running this at the command line and posting the output:

sudo apt-get -s dist-upgrade

(The -s makes this only a simulation, so it won't actually do anything...)

---

### Post by sleepytom on 2007-02-11
oops

---

