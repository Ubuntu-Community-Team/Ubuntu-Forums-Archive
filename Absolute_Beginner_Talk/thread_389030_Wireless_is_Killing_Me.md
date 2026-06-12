---
title: "Wireless is Killing Me"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by DVC on 2007-03-20
Hi.

I'm a total noob at this and trying to make my transition to linux so sorry if I sound like an idiot but I have been working on this for 16 hrs straight and starting to get a little disgruntled.

I'm dual booting XP and Ubuntu 6.06 and I am having a problem getting my wireless card working in Ubuntu.

I have one of those Linksys wireless gaming devices and I have no problem connecting to the internet on that by simply plugging in the ethernet cable, but I can not get my wireless pci card to work.  I have a linksys wmp54g.

I have installed ndiswrapper, ndisgtk, and the driver, plus I blacklisted the bcm43xx per instructions I found on the net.  In network settings it shows the wireless card and I have it set up DHCP.

The widows wireless drivers shows the driver installed and it says hardware present:yes which took me fover to figure out. ndiswrapper-l says driver present hardware present.

I have no idea WTF is going on I'm confused as hell and the internet still does not work if I can't get this working soon the wireless card is going out the window and I'll get one that works out of the box.

If anyone has any suggestions I would be very greatful.

---

### Post by stalkier on 2007-03-20
DVC first off, I understand your frustration. I have a Broadcom card and it seems like everytime I reboot my laptop I have to bring up the terminal to type in commands to get the WiFi working again. I created a txt file that has the following commands:

sudo rmmod bcm43xx

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo ifdown eth1

sudo ifup eth1

sudo dhclient

You will run these one at a time. I found this at:

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+edgy](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+edgy) 

I hope this helps bud. Don't give up.

---

