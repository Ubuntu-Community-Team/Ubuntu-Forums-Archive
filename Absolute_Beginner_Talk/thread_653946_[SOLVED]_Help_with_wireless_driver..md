---
title: "[SOLVED] Help with wireless driver."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2007-12-30
I just installed Ubuntu, however, I cannot get my wireless card to work because apparently it uses a "restricted proprietary" driver. I saw on another thread that if I was connected to the internet that the driver that I needed would be download automatically but that didn't work. Whenever I try to enable the driver in the restricted drivers wizard it gives me the following message: "The software source for the package bcm43xx-fwcutter" is not enabled". How do I fix this?

---

### Post by spiderbatdad on 2007-12-30
not sure but it looks like you need linux-restricted-modules-generic...take a look in synaptic. 
Also not sure but it looks like a card needing ndiswrapper and ndiswrapper-gtk, but i would looks for the restricted modules packages first and reboot, then try enabling again.

---

### Post by skaldicpoet9 on 2007-12-30
The linux-restricted-modules-generic package is already installed in the synaptic package manager. What is ndiswrapper and ndiswrapper-gtk?

---

### Post by spiderbatdad on 2007-12-30
[http://ubuntuforums.org/showthread.php?t=644231&highlight=bcm43xx-fwcutter](http://ubuntuforums.org/showthread.php?t=644231&highlight=bcm43xx-fwcutter)

---

### Post by anewguy on 2007-12-30
> **skaldicpoet9 said:**
> The linux-restricted-modules-generic package is already installed in the synaptic package manager. What is ndiswrapper and ndiswrapper-gtk?


Ndiswrapper, the required utilities and the optional ndisgtk (a gui front end to ndiswrapper) allow you to use Windows drivers within LInux for your wireless.  It would appear you have a Broadcom chipset wireless card, given what you have provided, but if you wouldn't mind please copy/paste the output of the following back here so we can verify:

(in a terminal window - Applications/Accessories/Terminal)

lspci   

This will list the known PCI devices on your computer, of which the wireless is hopefully one (unless it's a USB device).


There are many articles and threads both here and on the web for getting the Broadcom chipset wireless adapters working in Linux/Ubuntu.  With Gutsy (7.10) an attempt has been made to provide a driver, but it still requires a program to get the firmware.  Some people have had success with this (the restricted driver), other have not.  I would strongly suggest myself that you use ndiswrapper.  

Before we can give you exact instructions, we will need the output from above, and, if you know it, the maker/model/interface (USB, PCI, etc.) of the card.  With that information we should be able to help you.

:)

---

### Post by spiderbatdad on 2007-12-30
i believe ```
sudo lshw -C net
``` will provide better output for the info "anewguy" requested.

---

### Post by anewguy on 2007-12-30
> **spiderbatdad said:**
> i believe ```
sudo lshw -C net
``` will provide better output for the info "anewguy" requested.

Thanks for that!  I had someone tell me about that several months ago when I was doing some other debugging, but I have completely forgotten about it!  Thanks!:)

---

### Post by skaldicpoet9 on 2007-12-30
Ok so this is what I get when I enter in that command:

       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 02
       serial: 00:c0:a8:be:3f:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

I assume this is what you guys are looking for?

---

### Post by spiderbatdad on 2007-12-30
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by anewguy on 2007-12-31
The 4300 series is pretty easy to get working with ndiswrapper just as it is in synaptic without the need for the source and compilation you will see mentioned in some posts.  I'm posting here a link to another brand laptop how-to, but it is for the same wireless, so you can just follow the section there for getting wireless working.  Keep in mind that you may need a wired connection to do it (you need to install ndiswrapper and the ndiswrapper utilities and download the windows driver).  It is very easy:

[http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215]("http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215")

Let us know how it goes and if you have any problems!:)

---

### Post by skaldicpoet9 on 2007-12-31
Well, I got everything to work...I am on my wireless network with Ubuntu right now. However, now I have an enitirely different problem: [I screwed up my partition](http://ubuntuforums.org/showthread.php?t=654468)

---

### Post by forestpixie on 2007-12-31
can you mark this one solved as well then :)

---

### Post by skaldicpoet9 on 2007-12-31
Yep :)

---

