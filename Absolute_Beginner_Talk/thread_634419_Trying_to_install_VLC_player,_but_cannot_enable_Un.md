---
title: "Trying to install VLC player, but cannot enable Universe in Synaptic Package Manager"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by lewisskinner on 2007-12-07
Hey.  I trying to install the VLC media player, but it says I need to check I have the universe mirror, I tried to do this in the Synaptic package manager, but got this screen:

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-2.png[/IMG]

I tried entering ```
dpkg --configure -a
``` into the terminal, and got this: ```
lewis@Lewis-Jen:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```.  Any ideas?

---

### Post by julian67 on 2007-12-07
preface the command with sudo

```
sudo dpkg --configure -a
```

and enter your password when prompted.  You need root/admin privileges for package management.

---

### Post by spiderbatdad on 2007-12-07
looks like you're misisng sources. check /etc/apt/sources.list to make sure the sources are uncommented.

---

### Post by lewisskinner on 2007-12-07
> **julian67 said:**
> preface the command with sudo

```
sudo dpkg --configure -a
```

and enter your password when prompted.  You need root/admin privileges for package management.

```
lewis@Lewis-Jen:~$ sudo dpkg --configure -a
[sudo] password for lewis:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
lewis@Lewis-Jen:~$
```

Any ideas now?


> **spiderbatdad said:**
> looks like you're misisng sources. check /etc/apt/sources.list to make sure the sources are uncommented.

My sources.list:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by julian67 on 2007-12-07
The important part of the error message seems to be > E:_cache open failed

A problem with the cache might be due to different reasons like a hard disk error/failure, the hard disk might be full or almost full. It could also be caused by a corrupted package. I notice in your sources list you have your CD as a source. This may be imperfect. It's important to test the CD/DVD before it's used to make an install and also important to keep it in excellent condition if it's to be used as a package source. So I would go in this sequence:

check the free disk space

make a filesystem check and/or reboot

comment out the CD from the sources list and run the command again

reboot using the CD and check it.

---

### Post by lewisskinner on 2007-12-08
I have 6GB free in the /root

I checked the CD prior to installation.  it was fine, and I've not used it since.  I don't know why it'd be a source!

What do you mean "comment out"?

the final option i can see is reinstallation.  If I do reinstall Ubuntu, will I lose all my settings?  I have a separate /home partition, but don't I need to create a new username when I install?

---

### Post by spiderbatdad on 2007-12-08
before reinstalling try a few more things, maybe in this order:

```
sudo apt-get dist-upgrade && sudo apt-get update
```

```
sudo dpkg --configure -a
```
 If you have to reinstall, burn a new disk at slow speed, then verify it. good luck.

---

### Post by julian67 on 2007-12-08
> **lewisskinner said:**
> I have 6GB free in the /root

I checked the CD prior to installation.  it was fine, and I've not used it since.  I don't know why it'd be a source!

What do you mean "comment out"?

the final option i can see is reinstallation.  If I do reinstall Ubuntu, will I lose all my settings?  I have a separate /home partition, but don't I need to create a new username when I install?

source: it's a source of packages for your system.

comment out generally means you add the # symbol to the beginning of a line. This line is then ignored. If the problem lies with your CD then commenting out the line 

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
```

to read

```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
```

will prevent the cd from being used. You can do this and then run ```
sudo apt-get update
```

You didn't mention if you ran a filesystem check.

You should also re-check the integrity of the CD. Just because it was good in the past does not mean it's good now. Optical media can easily be damaged by heat, humidity etc and can give read errors just because a speck of dust or grit or a fingerprint is on it. 


I doubt you need to re-install. Suggest do as above and try again. If this fails you might want to check the cache is not corrupt or had some inadvertent change of permissions. The cache is located at /var/cache/apt/archives and should be owned and writeable by root. You should also check your privileges as a user. System>Users and Groups>yourusername>User Privileges.  Make sure  the box for administer the system is checked. 

If all else fails perhaps delete the entire cache. Google this first!

---

### Post by lewisskinner on 2007-12-08
> **julian67 said:**
> 
You didn't mention if you ran a filesystem check.


what is this, and how do I do one?

> **julian67 said:**
> 
You should also re-check the integrity of the CD. Just because it was good in the past does not mean it's good now. Optical media can easily be damaged by heat, humidity etc and can give read errors just because a speck of dust or grit or a fingerprint is on it. 


But I *never* use the CD!

And I can't edit the sources.list file - it says I haven't the necessary permissions.  Any ideas?

> **julian67 said:**
> If all else fails perhaps delete the entire cache. Google this first!
How?  Where is the cache?

---

### Post by julian67 on 2007-12-08
[Checking and Repairing File system with fsck]("http://adminschoice.com/docs/fsck.htm")

---

### Post by spiderbatdad on 2007-12-08
to  edit your sources.list, open the terminal:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by lewisskinner on 2007-12-09
> **spiderbatdad said:**
> before reinstalling try a few more things, maybe in this order:

```
sudo apt-get dist-upgrade && sudo apt-get update
```

OK, I ran this, but it just asked me to run

```
sudo dpkg --configure -a
``` as you also suggested.  I did this, and got the following:

```
lewis@Lewis-Jen:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
lewis@Lewis-Jen:~$ 

```

---

