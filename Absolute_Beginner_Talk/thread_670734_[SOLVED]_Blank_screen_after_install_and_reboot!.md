---
title: "[SOLVED] Blank screen after install and reboot!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-17
Hi, I have been trying to install ubuntu for a few days now. This is how far I have come: (I have a ATI Radeon Xpress 1200 Video Card.)

I have got into Ubuntu 7.10 by installing the fglrx-driver and then editing the /etc/X11/xorg.conf file to use fglrx instead of vesa which doesn't work. I have also tried with Kubuntu 7.10

In the Kubuntu's terminal I typed:
sudo apt-get install linux-restricted-modules-generic restricted-manager-kde
and then enabled the restricted driver fglrx.

I then installed the system and restarted the computer.

When I try to start it is just a blank screen and I can't do anything. It's the same thing for both Ubuntu and Kubuntu. If then get a commando line a type
startx
it says that the driver fglrx doesn't exist. And I can't donwload it now, because it then says
could not resolve gb.archive.ubuntu.com

I thought installing the driver in the system would last but it seems the driver only exist for the cd boot and I don't have it left then for the Installation boot.

Please help me to use either Ubuntu or Kubuntu...

---

### Post by spiderbatdad on 2008-01-17
you may need to create a directory and symbolic link. Have you seen these instructions?[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Mats_swe on 2008-01-17
> **spiderbatdad said:**
> you may need to create a directory and symbolic link. Have you seen these instructions?[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Yes I have, thanks.

But I can't use them after the installation since I then can't download stuff it seems.

---

### Post by Mats_swe on 2008-01-17
Is there any other way to install them on the installed version, then downloading them? Anyone?

---

### Post by spiderbatdad on 2008-01-17
there are fglrx drivers in synaptic...downloadable from the live cd ...xorg-driver-fglrx, and xorg-driver-fglrx-dev

---

### Post by Mats_swe on 2008-01-17
> **spiderbatdad said:**
> there are fglrx drivers in synaptic...downloadable from the live cd ...xorg-driver-fglrx, and xorg-driver-fglrx-dev

How do I download them???

---

### Post by Mats_swe on 2008-01-17
> **spiderbatdad said:**
> there are fglrx drivers in synaptic...downloadable from the live cd ...xorg-driver-fglrx, and xorg-driver-fglrx-dev

Hmm. But I'm now trying to boot without the cd. Should I try to put the cd in, download them, and then take it out again? I think it always want to connect to the internet.

---

### Post by spiderbatdad on 2008-01-17
can you boot into ubuntu desktop?

---

### Post by Mats_swe on 2008-01-17
> **spiderbatdad said:**
> can you boot into ubuntu desktop?

Yes I can by adding the fglrx file. But then I try to reboot I can't anymore. I just get a blank screen. And I get a commando line and try to start it says that it can't find fglrx.

---

### Post by spiderbatdad on 2008-01-17
from the desktop. you search synaptic package manger under Applications>>System>>Administration>>Synaptic package manager.  I'm not sure why you are trying to install this driver. Are you trying to enable advanced desktop effects? If so, you may just need to install xserver-xgl and compizconfig-settings-manager...both in synaptic. You might want to start by reinstalling the operating system if you havent gotten it working at all yet, but i guess that's really a last resort. Good luck...a little patience will pay off, and you'll learn something, too. After xserver-xgl you'll need to reboot.

---

### Post by spiderbatdad on 2008-01-17
if you are installing due to black screen after boot and install...you may have a problem with usplash.conf. spam your esc key and be patient...once your system loads, edit /etc/usplash.conf to a resolution that matches your screen...maybe 1024X768.

---

### Post by Mats_swe on 2008-01-17
> **spiderbatdad said:**
> from the desktop. you search synaptic package manger under Applications>>System>>Administration>>Synaptic package manager.  I'm not sure why you are trying to install this driver. Are you trying to enable advanced desktop effects? If so, you may just need to install xserver-xgl and compizconfig-settings-manager...both in synaptic. You might want to start by reinstalling the operating system if you havent gotten it working at all yet, but i guess that's really a last resort. Good luck...a little patience will pay off, and you'll learn something, too. After xserver-xgl you'll need to reboot.

I can't get into the installed, just the system on the live cd. But as they say - Changes I make there doesn't affect my installed system.

The radeon driver don't seem to be installed in the full system, just temporary in the live cd system. And I can't download it so I don't know how do get into the system again bacause I only get a blank screen.

---

### Post by spiderbatdad on 2008-01-17
try to boot without the live cd...hit the esc key several times once the blank screen comes up and be patient. it may take a few minutes. then edit /etc/usplash.conf if your system finally loads. if that doesn't work idk what?  Also, I believe you can mount your installed file system from the live cd, but I dont know exactly how to tell you to do this.

---

### Post by spiderbatdad on 2008-01-17
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

follow link to mounting ext3 file system with livecd

---

### Post by Nythain on 2008-01-17
so... i can only help so much here since i dont remember the exact line to add to /etc/apt/sources.list but ill get you most of the way there and hope someone else can elaborate more.

first... boot off hard drive install... i know this will take you to command line, thats ok.
once at command line, log in if not already.

after that, type
```

sudo nano /etc/apt/sources.list

```
this should open up your sources.list in nano, a command line text editor, with sudo privelages
sudo will ask for a password, its YOUR user password, not a root password, and it wont show you typing it, but it is typing it.

from here, im hoping someone can point out the line to add to the top to read from the cdrom drive as i dont think its there by default on a desktop install of ubuntu (impretty sure it the only non commented out option in most server or command line installs but thats a different story)

once you figure ouut the line to add to the top, add it, then hit control+x to exit, it will ask if you want to save changes, say yes, it will ask as what, default is sources.list, so just hit enter.

then, after all that put in the ubuntu cd and typ
```

sudo aptitude update

```
this will update your repo list with the packages available on the cd
after that all you should need to do is type the sudo apt-get (or aptitude) install line mentioned above to get the appropriate package i cant remember the name of and it will install it...

once you have the fglrx packages or whatever installed... then a simple
```

sudo dpkg-reconfigure xserver-xorg

```
should walk you through setting up a new xorg.conf file to get you going again... most of teh questions are either default answers or very simple and straight forward

hope any of that helped, im at work so i cant help mroe with specific commands and packages, but others should

and that sums up how to install something through aptitude using command line off of a cd

wich im saddend no one has suggested yet

---

### Post by Nythain on 2008-01-17
ok, so a little further research and instead of going the nano route it can be done easier with
```

sudo apt-cdrom add

```
that might/should add the cdrom to the /etc/apt/sources.list file automatically
then, to be more clear, the package installation would be
```

sudo aptitude xorg-driver-fglrx xorg-driver-fglrx-dev

```
according to a previous poster
there... even more helpfull info

---

### Post by Mats_swe on 2008-01-18
It finally worked:

[http://ubuntuforums.org/showthread.php?p=4161343#post4161343](http://ubuntuforums.org/showthread.php?p=4161343#post4161343)

---

