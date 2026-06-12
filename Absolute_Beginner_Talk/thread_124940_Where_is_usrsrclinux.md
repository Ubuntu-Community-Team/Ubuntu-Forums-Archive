---
title: "Where is /usr/src/linux??"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by chugru on 2006-02-02
Hi All...

I'm a new kubuntu Breezy user, having linux experience only with gentoo.

Wanted to look in **/usr/src/linux** and run **make munuconfig** just to see what I have loaded. To my surprise, there's nothing in **/usr/src/**:???: 

Would someone please explain to me where the directory I'm seeking might be located??

Thanks...

---

### Post by carlosqueso on 2006-02-02
you need to install the linux-tree package which contains the sources.   

type ```
sudo apt-get install linux-tree
``` to get it.  This will download the default ubuntu/kubuntu kernel tree, which you can then extract and poke around in with make menuconfig.

EDIT: put the RIGHT command in the code block

---

### Post by chugru on 2006-02-02
[QUOTE=carlosqueso]you need to install the linux-tree package which contains the sources.   

type ```
sudo apt-cache linux-tree
``` to get it.  This will download the default ubuntu/kubuntu kernel tree, which you can then extract and poke around in with make menuconfig.[/QUOTE]
Thanks for helping, but I just get....```
~$ sudo apt-cache linux-tree
Password:
E: Invalid operation linux-tree

```

Am I missing something?

---

### Post by carlosqueso on 2006-02-02
DOH! I was looking for the package name with apt-cache and messed up the typing.  the proper command is ```
sudo apt-get install linux-tree
``` sorry.  I'll edit my above post too in case people just read the first two.

---

### Post by chugru on 2006-02-02
[QUOTE=carlosqueso]DOH! I was looking for the package name with apt-cache and messed up the typing.  the proper command is ```
sudo apt-get install linux-tree
``` sorry.  I'll edit my above post too in case people just read the first two.[/QUOTE]
OK, thanks...

Now I get... ```
Media change: please insert the disc labeled
 'Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

```

Is this what I should expect?

---

### Post by carlosqueso on 2006-02-02
Ah...two questions.... 
1. do you have the Kubuntu CD? Apt is trying to get it from there.  So if you do, just put it in and press enter.
2. If you don't have the CD, do you have a working internet connection? then go and change your /etc/apt/sources.list file to the following: ```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

---

### Post by chugru on 2006-02-02
[QUOTE=carlosqueso]Ah...two questions.... 
1. do you have the Kubuntu CD? Apt is trying to get it from there.  So if you do, just put it in and press enter.
2. If you don't have the CD, do you have a working internet connection? then go and change your /etc/apt/sources.list file to the following: ```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```[/QUOTE]
I have the Kubuntu CD... It opens in Konquerer showing 8 folders:
dists
doc
install
isolinux
pics
pool 
preseed
ubuntu (shortcut)

---

### Post by chugru on 2006-02-02
i.e. the install CD, not the "Live" CD...

---

### Post by carlosqueso on 2006-02-02
cool...then just open a terminal and run ```
sudo apt-get install linux-tree
``` once more and it should work.

---

### Post by chugru on 2006-02-02
Awesome! I now have the following in **/usr/src/**:```
drwxr-xr-x   3 root root       72 2006-02-02 17:48 linux-patches
-rw-r--r--   1 root root 40351603 2006-01-16 14:42 linux-source-2.6.12.tar.bz2

```

Simply unzip/untar... 

Or is there more to it than that?

---

### Post by carlosqueso on 2006-02-02
nope...just untar that sucker (you'll need to use sudo before, since you don't have write permissions in that directory) and you'll see your kernel source

---

### Post by chugru on 2006-02-02
Getting there! **/usr/src/**:```
/usr/src$ ll
total 39447
drwxr-xr-x   3 root root       72 2006-02-02 17:48 linux-patches
drwxr-xr-x  19 root root      696 2006-01-16 14:40 linux-source-2.6.12

```

...But still no linux directory (unless I create it). Where do I run menuconfig?? 

...And why would **sudo make menuconfig** give the following: ```
$ sudo make menuconfig
sudo: make: command not found

```

Is **make** not an operational command??

Sorry for the many "lame" questions, but I'm trying to get this sorted out.

Thanks for helping!

---

### Post by deBaas on 2006-02-02
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

will aswer all your question.

btw. What has kernel stuff to to within "Absolute Beginners Talk"?

---

