---
title: "Install rar (Solved)"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by meestayenkins on 2005-12-04
I downloaded rarlinux-3.4.1.tar.gz and i extracted it but i cant figure out how to install it. Any help for a terminal newb?:smile:

---

### Post by aysiu on 2005-12-04
Sure. First let's get your sources.list up-to-date. 

1. Follow the instructions in the first link in my sig.

Okay. Let's say you downloaded it to your desktop: 

2. ```
cd Desktop
rm rarlinux-3.4.1.tar.gz
sudo apt-get update
sudo apt-get install rar
``` 3. You're done!

---

### Post by jrib on 2005-12-04
If you wish to be able to unrar archives as well you may also want to do:

2.5.
```
sudo apt-get install unrar-nonfree
```

---

### Post by IdolizingStewie on 2005-12-04
```
rar e archive.rar
```
This will extract archives, so I don't think you need unrar if you have rar.

---

### Post by meestayenkins on 2005-12-04
```
keith@ubuntu:~/Desktop$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```

I've already added the extra repositories and update the apt-get.  So I downloaded the rarlinux-3.4.1.tar.gz from rarlabs. I want to just install that. So I have the TGZ file on my desktop, how do I install it through terminal?

---

### Post by aysiu on 2005-12-04
Frankly, I find that hard to believe, seeing as how I just did this a minute ago: ```
 sudo apt-get install rar
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  unrar
The following NEW packages will be installed:
  rar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 246kB of archives.
After unpacking 500kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/multiverse rar 3.30-2 [246kB]
Fetched 246kB in 4s (55.5kB/s)

Preconfiguring packages ...
Selecting previously deselected package rar.
(Reading database ... 127012 files and directories currently installed.)
Unpacking rar (from .../archives/rar_3.30-2_i386.deb) ...
Setting up rar (3.30-2) ...
``` Something must be off with your repositories.

Since you're insistent on installing it from source, though, check out [this link](http://www.psychocats.net/linux/installingsoftware.php), especially the bottom bit.

Keep in mind, though, that when you install from source:
1. No dependencies are met--you'll have to install those all separately.
2. You no longer have a centralized way to upgrade your installed software.

Best of luck, though--after all, the bottom line is that you want it installed, no matter how it gets done.

---

### Post by meestayenkins on 2005-12-04
Well I definitely wanna do things the best way, so heres my sources.list. See anything wrong? 

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```

I just replaced my sources.list with the one in your signature. I updated apt-get then tried to install rar and got this
```
keith@ubuntu:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  rar: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
  unrar: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multivers Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multivers_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by aysiu on 2005-12-04
[QUOTE=meestayenkins]Well I definitely wanna do things the best way, so heres my sources.list. See anything wrong?[/quote] Yes. You don't have the multiverse repositories enabled. Please follow the instructions in the first link in my sig. They're easy to follow, and they make a back up copy of your old sources.list, so you don't have anything to lose.

---

### Post by meestayenkins on 2005-12-04
okay figured it out. i had to do this 'apt-get -f install' problem fixed.

Oh and thanks for all the help :-D sorry to be a pain in the ass, i'm a newbie :-p

---

### Post by aysiu on 2005-12-04
I'm just glad it all worked out.

---

### Post by jrib on 2005-12-05
[QUOTE=IdolizingStewie]```
rar e archive.rar
```
This will extract archives, so I don't think you need unrar if you have rar.[/QUOTE]

oh, ok I'll believe that.  I thought that since rar suggested unrar, it might be necessary.  I never installed that rar package because it's description reads: "This program is shareware and you must register it after 40 days of use."  Can anyone shed some light on that?  Does it continue to work after 40 days?  How would one register?

---

### Post by phantomlord on 2005-12-11
I'm also having trouble installing rar.
This is my sources.list

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
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

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```


And this is what happens when I try to install rar.

```
sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```

Anyone has any idea what is wrong?

---

### Post by aysiu on 2005-12-11
Did you do a ```
sudo apt-get update
``` first?

---

### Post by phantomlord on 2005-12-11
yes, I did.

---

### Post by aysiu on 2005-12-11
I don't know what else to tell you. My sources.list looks just like yours, and it worked fine (I did this less than a minute ago): ```
 sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  unrar
The following NEW packages will be installed:
  rar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 246kB of archives.
After unpacking 500kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/multiverse rar 3.30-2 [246kB]
Fetched 246kB in 2s (105kB/s)

Preconfiguring packages ...
Selecting previously deselected package rar.
(Reading database ... 122235 files and directories currently installed.)
Unpacking rar (from .../archives/rar_3.30-2_i386.deb) ...
Setting up rar (3.30-2) ...
```

---

