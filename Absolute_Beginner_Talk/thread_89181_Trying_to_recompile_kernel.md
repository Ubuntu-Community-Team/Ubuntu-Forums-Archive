---
title: "Trying to recompile kernel"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by gear_ratio on 2005-11-12
So I just installed Ubuntu Breezy, and wanted to compile my own kernel. However, I've run into problems with downloading the linux-source

I'm following instructions found at [https://wiki.ubuntu.com/KernelHowto#head-4cab2b0e17252fc39575ef014ca3c5ed64201719]("https://wiki.ubuntu.com/KernelHowto#head-4cab2b0e17252fc39575ef014ca3c5ed64201719")
 and get past the "Obtaining the source step". Here is the output from this command 

```
<bash>apt-cache search source 2.6
alsa-base - ALSA driver configuration files
linux-image-2.6.12-9-386 - Linux kernel image for version 2.6.12 on 386.
```

Notice that it says "linux-image" and NOT "linux-source". When I proceed with 

```
<bash>sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source
```

or, when I try

```
<bash>sudo apt-get install linux-image-2.6.12-9-386
Reading package lists... Done
Building dependency tree... Done
linux-image-2.6.12-9-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

How i do get the source Code?

---

### Post by 23meg on 2005-11-12
To learn which kernel you're using, type ```
uname -r
``` and then download the linux-source package that corresponds to your kernel. It's most likely "linux-source-2.6.12".

[This guide]("http://www.ubuntuforums.org/showthread.php?t=85064") to kernel compilation is aimed at beginners; you might find it helpful.

---

### Post by tseliot on 2005-11-12
You have to enable all the repositories but the backports (which are not necessary for this).

Type:

[QUOTE=]sudo gedit /etc/apt/sources.list (or sudo nano /etc/apt/sources.list)[/QUOTE]

Then uncomment, i.e. remove the "##" before the lines starting with "deb-http" or "deb-src". See the example (leave the backports as they are):

[QUOTE=]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

##deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
##deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free[/QUOTE]

Then save the file and exit.

Type:

[QUOTE=]sudo apt-get update[/QUOTE]

Then, if you want the kernel source and its patches

[QUOTE=]sudo apt-get install linux-tree[/QUOTE]

Enjoy!

---

