---
title: "graphics problem"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-06
I have an ATI Rage 128 RF/SG AGP graphics card (circa 2000-01) in the machine I've installed Ubuntu. I'm having some problems with it however, when I run some graphics software or type the command 'glxgears' into the terminaI get the following output:

glxgears
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Illegal instruction

A similar thing will happen when I run an application except it will core dump at the 'Illegal Instruction' line instead. I believe I need to update my drivers however according to the ATI webpage I should have the foolowing packages for Debian 3.0r5 (Ubuntu is not listed in the Support Chart pdf, [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27):](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27):)

X.Org 6.8.2
XFree86 4.1.0, 4.2.0 and 4.3.0

I have the following packages listed in Synaptic which I believe are relevant:

xorg-common 6.8.2-77 (That should be okay)
libXxf86vm 7.0.0-2
libXxf86misc 7.0.0-2
libXxf86dga 7.0.0-3

I don't understand how my XFree86 packages are a full 3 versions ahead leading me to believe I'm looking at the wrong packages in Synaptic. Which ones should I be looking for? Is my graphics card too old (I hope not)? How can I resolve it? I really need to run these graphics apps, any help would be greatly appreciated!

---

### Post by richbarna on 2006-05-06
Hi cl3ellio,
Hmm, many ati posts these days, I can only make a couple of "suggestions" as Linux-Compatible says that your card should be ok :-
[http://www.linuxcompatible.org/ATI_Rage_Pro_128_c9886.html](http://www.linuxcompatible.org/ATI_Rage_Pro_128_c9886.html)

1. You could change the xorg.conf file to go for the "vesa" driver instead of the "ati" driver, but that is known to stop 3d acceleration
Look on the repositories for xserver-xorg-driver-vesa
2. Download an ati Linux driver here :-
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Sorry I can't help more

Good Luck : )

---

### Post by richbarna on 2006-05-06
Take a look at this as well :-
[http://ubuntuforums.org/showthread.php?t=171008](http://ubuntuforums.org/showthread.php?t=171008)

---

### Post by cl3ellio on 2006-05-06
I tried following the instructions that we're posted on the thread that was passed along above. First I try and install the kerneal linux-386 but it tells me that every thing is up to date, OK. When I try and install the 'xorg-driver-fglrx' package I get the following:

~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx

So I'm still trying to figure this problem out, the ATI compatibility web page says I'm okay, but thats only one entry.

---

### Post by richbarna on 2006-05-06
Hi cl3ellio,
> sudo apt-get install xorg-driver-fglrx works ok for me, I think you need to allow restricted and multiverse in your source list.
To do this :-
> sudo gedit /etc/apt/sources.list
Your "gedit" text editor will open. You can uncomment (remove the two ##'s in front of the repository URL's) or delete it all and copy and paste this :-
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

## created by arnielistenadded


Then :-
> apt-get update
and :-
> sudo apt-get install xorg-driver-fglrx

Should work this time.
good luck

---

### Post by cl3ellio on 2006-05-06
Buya! Finally its working! Thanks!

---

### Post by richbarna on 2006-05-06
No probs : )
Que vayas bien ; )

---

