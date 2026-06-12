---
title: "Package problems"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-08-24
I have tried to find a post on this and can not... I have read several and none of the recommendations seem to help the problem...I am really stuck

running any type of package upgrade all return some derivation of: ": Sub-process /usr/bin/dpkg returned an error code (1)"
(this snip from aptitude dist-upgrade)

[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.20-15-generic (2.6.20-15.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.20-15.27 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.20-15.27 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-15-generic:
 linux-restricted-modules-2.6.20-15-generic depends on linux-image-2.6.20-15-generic; however:
  Package linux-image-2.6.20-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-15-generic
 linux-restricted-modules-2.6.20-15-generic
E**: Sub-process /usr/bin/dpkg returned an error code (1)**
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-15-generic:
 linux-restricted-modules-2.6.20-15-generic depends on linux-image-2.6.20-15-generic; however:
  Package linux-image-2.6.20-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.20-15-generic[/INDENT]


Any suggestions?

Should i just reload?

thanks in advance....

---

### Post by CallMeDerek on 2007-08-24
now running dselect and doing an upgrade i get a pop up blue dialog during update that reads:

You are running a kernel (version 2.6.20-16-generic) and attempting to remove the same version. This is a potentially disastrous action. Not only will                      &#9474;
 &#9474; /boot/vmlinuz-2.6.20-16-generic be removed, making it impossible to boot it, (you will have to take action to change your boot loader to boot a new kernel), it will also   &#9474;
 &#9474; remove all modules under the directory /lib/modules/2.6.20-16-generic. Just having a copy of the kernel image is not enough, you will have to replace the modules too.      &#9474;
 &#9474;                                                                                                                                                                             &#9474;
 &#9474; I repeat, this is very dangerous. If at all in doubt, answer Yes. If you know exactly what you are doing, and are prepared to hose your system, then answer No.


EEEEKS!  what have i messed up?

---

### Post by annda on 2007-08-24
what exactly are you trying to do? upgrade edgy to feisty? what is the exact command you are using and what is your current sources.list?

---

### Post by wormser on 2007-08-24
I am not sure what is going on, but I found some info and a resolution for this error you are getting"E: Sub-process /usr/bin/dpkg returned an error code (1)"

In the 2nd post on this [forum]("http://www.linuxquestions.org/questions/showthread.php?s=&forumid=9&threadid=171107")

> After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

That resolved that error message according to the thread.

---

### Post by CallMeDerek on 2007-08-24
I saw that post as well th -f caused the same error....

The order of events went something like this...

Idid a standard package update check in Kubuntu Adept - indicated new updates
pulled the updates and during the install i noticed it wanted to remove some 250 packages 
i freaked and canceled


Where I stand now is it seems using dselect and going through the updates, install and remove options all worked after responding "no" to the scary message above.

No more error one apt and now standard GUI Adept update seems to be working

Hmmmm fixed???  Hard to say but the error is gone.

any other thoughts?



source file:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

# PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#AUTOMATIX REPOS START
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
#AUTOMATIX REPOS END
deb [http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/) ./

---

### Post by CallMeDerek on 2007-08-25
Ok - fixed till i rebooted....

now grub will not boot saying it cant find the version 2.6.20-16 image

I am sure this all ties back to /boot/vmlinuz-2.6.20-16-generic being corrupt.

Is there some way i can just repalce this file and rest my packages?  Or do i just reinstall?

---

### Post by zachalekos on 2007-08-28
what's the deal with this?

---

### Post by schorsch on 2007-08-28
Did you type
```
sudo apt-get update
```
before? The content of third party repos can change more often than the content of the official repos so you need to have a actual package list when installing packages from third party repos.

---

### Post by zachalekos on 2007-08-28
> **schorsch said:**
> Did you type
```
sudo apt-get update
```
before? The content of third party repos can change more often than the content of the official repos so you need to have a actual package list when installing packages.

Happens again when I try to install a new package. Thanks for the quick response.

---

### Post by schorsch on 2007-08-28
As this package exists in the official repos
```
~/$ aptitude show bcm43xx-fwcutter
Package: bcm43xx-fwcutter
New: yes
State: not installed
Version: 1:006-1
Priority: optional
Section: universe/utils
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 119k
Depends: libc6 (>= 2.5-0ubuntu1), debconf (>= 0.5) | debconf-2.0
Recommends: wget | curl
Description: Utility for extracting Broadcom 43xx firmware
 fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files. 
 
 The project page is http://bcm43xx.berlios.de/
```
I would suggest to temporary disable the repos containing "boredklink" by adding a "#" (without the quotes!) to the start of lines and then do
```
sudo apt-get update
```
After this is done try again .... whatever you did as this is not clear from your attachment .....

---

### Post by zachalekos on 2007-08-28
it doesn't work, I'm afraid. still show an error message when I install a new package

---

### Post by schorsch on 2007-08-28
Well, o.k., next try:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```
and try again what ever you want.

---

### Post by zachalekos on 2007-08-28
this is what comes out...

---

### Post by schorsch on 2007-08-28
Hmm ......
```
sudo apt-get -f remove
```

---

### Post by zachalekos on 2007-08-28
the same ... :(

---

### Post by schorsch on 2007-08-28
What is the output of
```
cat /etc/apt/sources.list
```

---

### Post by zachalekos on 2007-08-28
alex@alex-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

---

### Post by schorsch on 2007-08-29
Sorry, I do not have any more ideas ..... I see nothing weird in your sources list ... perhaps some other guy on this forum can help you ...

---

