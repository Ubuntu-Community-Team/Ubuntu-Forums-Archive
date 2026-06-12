---
title: "Basic Wireless Help"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jonwatts on 2007-11-21
hi
i just inherited a nice dell latitude C640, which had no built in wireless card, so i bought one.  it is a Dlink super G Mimo wireless adapter, and the ubuntu list of working wireless cards includes it.  So... here I am with an installation CD that seems to only work for windows and a wireless card with no lights flashing.  Can anyone tell me where to go from here?

thanks!
jon

ps the OS is ubuntu 7.04

---

### Post by victorgreen on 2007-11-21
The installation cd that came with you wifi card wont have linux drivers on it. The drivers should be in kernel if the card is supported/does work with linux/ubuntu. Does ubuntu recognize the card/does networkmanager show any wireless networks?

As far as I know, ubuntu doesnt light up the little wifi light like windows does. Something in the software, although this may depend on wifi card. It suffices to say that jsut cause the little wifi light isnt on doesnt mean you dont have wifi.

---

### Post by jonwatts on 2007-11-21
hi.
thanks for the reply.

As far as I can tell, ubuntu does not recognize the card.  That is, I went into the network manager and it just showed me only the possibilities for ethernet and dialup but not wireless.  Can I search for the drivers?  or something?

When I was shopping for cards, many of them said that they were only supported for windows, and many of those were on the list at the ubuntu site (of supported cards).  But idunknow... should i have listened to Dlink or Ubuntu?

jon

---

### Post by Partyboi2 on 2007-11-21
Can you post the output of this command:
```
 lshw -C network
```
This will tell if the card is being detected

---

### Post by jonwatts on 2007-11-21
*-network UNCLAIMED
description: Ethernet controller
product: AR5005VL 802.11bg Wireless NIC
vendor: Atheros Communications, Inc.

and so on, and so forth.  This means that the computer recognizes it, yes?  If so, hurrah!  what do I do now?

thanks for your patience,
jon

---

### Post by H3retic on 2007-11-21
This might not be the most useful thing, but...

I couldn't get wireless working with 7.04.  Then, I switched to 7.10 and it works just fine, no hassle.  I suggest you upgrade, my friend.

---

### Post by jonwatts on 2007-11-21
oh, but I'm almost... there...  right?!  

Why isn't the card showing up in my network settings?  (all i see is "wired connection" and "modem connection")  Where is this illusive "network manager" program?  What is the meaning of life?

love,
jon

---

### Post by jonwatts on 2007-11-21
oooo kkkkk.  I've got nothing better to do, i guess.  I'll let you know how the installation goes.

peace
jon

---

### Post by Partyboi2 on 2007-11-21
have you tried using madwifi 
 [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
or  ndiswrapper [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)

You will probably have to use one of those 2 methods to get your wireless setup.

---

### Post by LaneLester on 2007-12-13
I'm running Gutsy, and I'd like to know the steps to get my Netgear 401 working. Here's what lshw shows:

  *-network               
       description: Card
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 1
       resources: irq:3
  *-network
       description: Ethernet interface
       product: EN-1216 Ethernet Adapter
       vendor: Accton Technology Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 11
       serial: 00:d0:59:61:05:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.100 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0_rename
       serial: 00:09:5b:49:fe:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.3.6 multicast=yes wireless=IEEE 802.11b

Lane

---

