---
title: "KDE or GNome"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by utab on 2006-02-23
Dear,

As it is obvious from the thread header. I am using Gnome which is unstalled with Ubuntu but also would like to experiment with KDE(curious about that.). What is your opinion about KDE. 

And how to install KDE and get that working on Ubuntu.

Thx.

---

### Post by frodon on 2006-02-23
To install KDE open a terminal and type : ```
sudo apt-get install kde-desktop
```Then in the login screen click on "session" and choose KDE or GNOME ... up to you ;)

---

### Post by utab on 2006-02-23
[QUOTE=frodon]To install KDE open a terminal and type : ```
sudo apt-get install kde-desktop
```Then in the login screen click on "session" and choose KDE or GNOME ... up to you ;)[/QUOTE]

I got this 

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package kde-desktop

Thx

---

### Post by Jucato on 2006-02-23
Um... if I'm not mistaken, there is no kde-desktop metapackage.
you can either install the kde metapackage to install the default KDE settings
```
sudo apt-get install kde
```
or kubuntu-desktop to install the Kubuntu KDE settings (those the Kubuntu devs chose to include)
```
sudo apt-get install kubuntu-desktop
```
I recommend that you take careful note of the things that will be installed using either of these commands, to make uninstalling easier.

---

### Post by utab on 2006-02-23
[QUOTE=Fenyx]Um... if I'm not mistaken, there is no kde-desktop metapackage.
you can either install the kde metapackage to install the default KDE settings
```
sudo apt-get install kde
```
or kubuntu-desktop to install the Kubuntu KDE settings (those the Kubuntu devs chose to include)
```
sudo apt-get install kubuntu-desktop
```
I recommend that you take careful note of the things that will be installed using either of these commands, to make uninstalling easier.[/QUOTE]

This is the result of the first command namely, ...kde

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kdesdk but it is not going to be installed
E: Broken packages

That is obvious that I have a problem with the sources. :(

Thanks

---

### Post by frodon on 2006-02-23
Run a : ```
sudo apt-get update
```And post your source.list file here, i will check that you have all the repositories enabled : ```
sudo gedit /etc/apt/sources.list
```Details about adviced sources.list repositories here : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by wombat20 on 2006-02-23
I just used Synaptic and searched for KDE.

Remember that both are quite customisable, so have a fiddle around with each before you decide for certain.  The lightweight XFCE might be worth trying too.

---

### Post by utab on 2006-02-23
[QUOTE=frodon]Run a : ```
sudo apt-get update
```And post your source.list file here, i will check that you have all the repositories enabled : ```
sudo gedit /etc/apt/sources.list
```Details about adviced sources.list repositories here : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)[/QUOTE]

the first is OK and 

Get:1 [http://ftp.belnet.be](http://ftp.belnet.be) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/restricted Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [37.7kB]
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/main Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/restricted Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/universe Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://ftp.belnet.be](http://ftp.belnet.be) breezy/multiverse Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [28.3kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [1560B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [11.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4747B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [380B]
Fetched 117kB in 1s (61.4kB/s)
Reading package lists... Done

there goes the sources.list

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates

deb [http://ftp.belnet.be/linux/ubuntu/ubuntu](http://ftp.belnet.be/linux/ubuntu/ubuntu) breezy main restricted universe multiverse
deb-src [http://ftp.belnet.be/linux/ubuntu/ubuntu](http://ftp.belnet.be/linux/ubuntu/ubuntu) breezy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

## libdvdcss2, w32codecs
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main restricted universe multiverse

## jedit
# deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
# deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

Thx.

---

### Post by Sp@z on 2006-02-23
KDE is beautiful! But runs like as* on my laptop since it is a bt older. I am running Gnome and I like it, but even it is a lil heavy on my laptop. I would run xfce but I hate MICE, creeps me out just starting it.

---

### Post by aysiu on 2006-02-23
[QUOTE=utab]
there goes the sources.list```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates

deb http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse
deb-src http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## libdvdcss2, w32codecs
# deb ftp://ftp.nerim.net/debian-marillat/ etch main

# deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

## jedit
# deb http://dl.sourceforge.net/sourceforge/jedit ./
# deb-src http://dl.sourceforge.net/sourceforge/jedit ./

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
# deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted

deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

```[/QUOTE] The # sign means "ignore this line," so basically, these are the sources that are active in your sources.list: ```
deb http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse
deb-src http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
``` That's a rather odd sources.list, I have to say. Try the first link of my sig.

---

### Post by frodon on 2006-02-23
utab, you should add those directories in your source.list file, but all the needed information are in the link i gave you : ```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
```

---

### Post by utab on 2006-02-23
[QUOTE=aysiu]The # sign means "ignore this line," so basically, these are the sources that are active in your sources.list: ```
deb http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse
deb-src http://ftp.belnet.be/linux/ubuntu/ubuntu breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
``` That's a rather odd sources.list, I have to say. Try the first link of my sig.[/QUOTE]


No use still can not install 

sudo apt-get install kde 

giving this error

Reading package lists... Done
Building dependency tree... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package kde has no installation candidate

Thx.

---

### Post by utab on 2006-02-23
[QUOTE=frodon]utab, you should add those directories in your source.list file, but all the needed information are in the link i gave you : ```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
```[/QUOTE]

Here is the sources.list and these lines you mentioned are there 

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

Thx.

---

