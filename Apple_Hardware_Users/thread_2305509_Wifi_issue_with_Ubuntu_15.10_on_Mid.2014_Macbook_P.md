---
title: "Wifi issue with Ubuntu 15.10 on Mid.2014 Macbook Pro"
date: 2015-12-06
forum: Apple Hardware Users
---

### Post by vladi3 on 2015-12-06
Hello community,

Its been a while since I was dreaming of making transition to Ubuntu. I am a first time user, and it took me great 8 hours to set up my first system.
I've managed to find work arounds on every issue I've faced with installation, apart from this one:

I am experiencing no wifi what so ever, I've been read through numerous threads on this forum and tried different .deb versions, but literally nothing helped..
I've just deleted all drivers that I've tried to install with:
sudo apt-get remove bcmwl-kernel-source

If i go to Software and updates, there is nothing listed there in additional drivers.

So from what i know, I am running 64bit version

By running following command:
lspci -nn

I get:
Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

So from what I understand on this forum I have to install additional driver which suppose to be downloaded from somewhere and it should be in format of .deb
Is here anyone who can help? Once again I am setting this up on MacBook Pro Mid.2014 Retina. I am far away from being professional in any of the terms you might use, so the easier you explain the best :)

Thank you fellas!

---

### Post by BobUgh on 2015-12-08
To 15.10 experienced users: Isn't there a graphical way on 15.nn to search for additional drivers?

Vladi3, Since WiFi isn't working, I think you will need to be connected to the internet some other way when searching for drivers. There should be some icon like "System Settings" > "Additional Drivers" ; at least there was on older Ubuntu versions, I haven't used version 15.n 

You have done awfully well if you have it working as a first time user and it only took you 8 hours and you have it installed it on a Mac. Dual or single boot? But may I ask, why did you choose 15.10? Isn't 14.04 LTS recommended as that is more stable and will be supported longer?  As someone new, you probably were not aware of that. Is your Macbook listed on [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) if so which one? Now I see a 14.10 there for one system; so now I am confused!

But if wireless is your only problem, and you are able to install the drivers and get it working, I suggest you stick with 15.10

---

### Post by MikeBraxner on 2015-12-09
@Vladi3 ... This should be relatively easy to sort out.

Simply insert the thumbdrive you used for your install, open Files, and go to 
***[Thumbdrive]/pool/main/d/dkms/***
and, double click on ***dkms_2.2.0.3-...deb*** 

This will bring up the Software Center ... just tell it to install. Once that is finished, close the Software center.

In Files, navigate to 
***[Thumbdrive]/pool/restricted/b/bcmwl/***
and double click on ***bcmwl-kernel-source_...deb***

Confirm the install again in Software Center, and wait until its finished. Now Close the Software Center, and select your network of choice in the network monitor (top bar, right hand side). Easy piecy ;-)

_______________________________________

If you don't have your thumbdrive anymore--or installed Kubuntu--you can also use the ISO file you downloaded. In this case, open a terminal, and follow this pattern

```
sudo mkdir /media/cdrom
sudo mount -t iso9660 -o loop [/path/to/your/iso] /media/cdrom
sudo apt-cdrom -m -d=/media/cdrom add
sudo apt-get -y install bcmwl-kernel-source
sudo umount /media/cdrom
sudo rmdir /media/cdrom
```
... and select your network.

Hope this helped.

---

### Post by dellboy56 on 2016-01-02
Try installing dkms from usb pool/main/d/dkms then pool/restricted/b/bcmwl install shouls get you up and running

---

