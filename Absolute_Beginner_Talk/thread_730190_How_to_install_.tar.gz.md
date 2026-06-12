---
title: "How to install .tar.gz"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by VyperX on 2008-03-20
Hello, I  am a noob at ubuntu and I want to learn how to install .tar.gz, it is very difficult for me, specially when I am trying to fix my network and someone says that I need to download something like madwifi and it is .tar.gz so I get very desperate...,

thanks

---

### Post by Shabbro on 2008-03-20
I reccomend [this guide]("http://monkeyblog.org/ubuntu/installing/") to learn how to install almost any package in ubuntu

I think what you need to look at on there is the "Installing a package manually" section [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

Then scroll down to the "Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)" section

---

### Post by aysiu on 2008-03-20
> **Shabbro said:**
> I reccomend [this guide]("http://monkeyblog.org/ubuntu/installing/") to learn how to install almost any package in ubuntu
I second the motion. If you don't compile from source for fun, a .tar.gz should be the last resort.

---

### Post by munch3 on 2008-03-20
if ure a newbie, just dont install tar.gz stuff.U can find 95% of stuff in synaptic package manager or addremove programs or getdeb.net for a deb package

---

### Post by k33bz on 2008-03-20
I thought mad-wifi was in the repos?

---

### Post by Oldsoldier2003 on 2008-03-20
> **munch3 said:**
> if ure a newbie, just dont install tar.gz stuff.U can find 95% of stuff in synaptic package manager or addremove programs or getdeb.net for a deb package

i don't like get deb because

> Packaging
Redundant effort should be avoided by checking if debian packaging build files are already available from Debian based sources, when not available debian package build files mus be created, creating packages using checkinstall should be avoided once they do not provide proper dependency checking.
*Note: The GetDeb team may not follow the Debian/Ubuntu packagning guidelines meaning you should not expect the same level of quality control as you get from those. On the other hand you will be able to get usefull packages that will hardly get into Debian/Ubuntu due to policy constraints.*[http://www.getdeb.net/about.php](http://www.getdeb.net/about.php)

But with that said Get Deb is a great resource if you do not want to compile your own packages

---

### Post by forestpixie on 2008-03-20
Can I just say that if the OP is trying to get the network going the repos aren't going to be much fun - he won't be getting build-essential either :(

---

### Post by Linux_Man on 2008-03-20
I thought build-essential was on the CD? Might not be right but if I remember right it kept prompting me for the CD when I tried to install that.

---

### Post by forestpixie on 2008-03-20
my bad

---

### Post by VyperX on 2008-03-21
> **munch3 said:**
> if ure a newbie, just dont install tar.gz stuff.U can find 95% of stuff in synaptic package manager or addremove programs or getdeb.net for a deb package

Yes I am a newbie and I want to learnbecause I dont wnna be a newbie anymore

---

### Post by logos34 on 2008-03-21
> **Linux_Man said:**
> I thought build-essential was on the CD? Might not be right but if I remember right it kept prompting me for the CD when I tried to install that.

You're right--it is.  I didn't think it was until one day I finally checked.  I wish someone would tell me why, if it's on the cd, it doesn't install by default?

---

### Post by VyperX on 2008-03-22
> **logos34 said:**
> You're right--it is.  I didn't think it was until one day I finally checked.  I wish someone would tell me why, if it's on the cd, it doesn't install by default?

Yeah that's weird

---

### Post by linuxtoindia on 2008-03-22
same problem here i have downloaded kalkulate a software
at ''/home/akshay/Desktop/kalculate-pro60.tgz''
how to install it?

---

### Post by logos34 on 2008-03-22
> **linuxtoindia said:**
> same problem here i have downloaded kalkulate a software
at ''/home/akshay/Desktop/kalculate-pro60.tgz''
how to install it?

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

make sure to read the README.txt and/or INSTALL.txt files first.

---

### Post by linuxtoindia on 2008-03-23
the read me text 

''          Kalculate PRO Version 3.2
             
                  How to install Kalculate in your machine

   To install Kalculate on your machine, just follow the following steps:

    1. First, the obvious : You will need Linux on your PC. OpenLX Linux 11.0.
    2. Login with your id and required password.
    3. [user@localhost user]$ su <enter>
    4. [root@localhost user]# mount /mnt/cdrom <enter>
    5. [root@localhost user]# cd /mnt/cdrom/kalculate <enter>
    6. [root@localhost kalculate]# ./install-admin <enter>

   If you are in text-mode then start your X window before running kalculate. Kalculate can be installed in text-mode.

    7. [user@localhost user]$ kalculate-admin <enter>

   While using kalculate, you will require kalculate authentication password. It is 123.''


what to do now?

---

### Post by VyperX on 2008-03-24
what are you trying to install?

---

### Post by forestpixie on 2008-03-24
It's some financial software - think it's rpm based - not much information.

[http://ubuntuforums.org/showthread.php?t=731982](http://ubuntuforums.org/showthread.php?t=731982)

---

### Post by VyperX on 2008-03-25
This has nothing to do with this thread but how do I update openoffice?

---

