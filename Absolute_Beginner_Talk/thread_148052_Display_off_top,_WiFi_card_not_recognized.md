---
title: "Display off top, WiFi card not recognized"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-03-21
These are my first experiences and problems with Linux.

I have a Compaq Presario 1688 laptop.  

1.  After loading Ubuntu 5.10 from the CD my display has the problem that the menu bar goes over the top.  I see a little more than the bottom half of menu words such as Applications.  

2.  I have a M$ MN-520 802.11b wireless card that isn't recognized.  

Any help would be appreciated.

---

### Post by gnu2tux on 2006-03-27
Firstly, sounds like you have some sort of problem with your monitor settings.

Press Ctrl+Alt+F1 or F2 and it will take you to login prompt (text mode)
login as normal

```

$sudo bash
Password: <your pass>

#/etc/init.d/gdm stop (or kdm stop if using kubuntu)
#dpkg-reconfigure xserver-xorg

```

You will now go through a series of menus to set up your graphics card and monitor. Try and get the refresh and max resolution settings of your monitor from a manual or the net somewhere. You will need to put these in. Try going for the Medium skill settings on the monitor side before trying Beginner or Advanced.

To the wireless. Rather than repeat myself, check out my guide and let me know how you are getting on after then:

[http://www.linuxnewbieguide.org/ht-wififallback.php]("http://www.linuxnewbieguide.org/ht-wififallback.php")

Regards,

Ali.

---

### Post by JEBB on 2006-03-31
I have since found that changing the refresh rate to the lowest on the menu - 59 - gave me a satisfactory screen.  Only a little of the menu words are still off the top of the screen.

I solved one part of the WiFi problem by buying a new card, one that was in one of the lists I found here, the Zonet ZEW1501.  It worked right out of the box.  I can get to the Internet via my WEP protected Apple Extreme Base Station without a problem.  

My one remaining issue is printing on a USB printer attached to the AEBS.

---

### Post by gnu2tux on 2006-03-31
I don't know anything about the AEBS, however I do have a wifi network and share a printer between PCs, this is how I do it:

Plug my USB printer into my PC.
Set up the PC for a static IP address on the wifi router and in the network properties in ubuntu. This way, the printer can always be located by the same address.
Set up your printer either using the printer setup tool, or by using the cups web interface at [http://127.0.0.1:631](http://127.0.0.1:631).

You must set it to allow connections from other IP addresses on the network, but after that, any machine capable of using CUPS can talk to the printer through that PC.

Hope this helps.

Al.

---

