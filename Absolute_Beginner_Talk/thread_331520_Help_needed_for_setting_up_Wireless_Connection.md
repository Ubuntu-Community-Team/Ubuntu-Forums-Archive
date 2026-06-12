---
title: "Help needed for setting up Wireless Connection"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by boilermaker on 2007-01-04
Hi Guys:

I recently installed Ubuntu into my laptop [Dell Inspiron B 130] and have been trying hard to make my wireless connection work. 

Hardware details,

Dell Wireless 1370 WLAN Mini-PCI Card
Manufactured by Broadcom

Also what is ndiswrapper stuff? how to install it!

I would greatly appreciate if you can help me.

Thanks

---

### Post by MasterOfDisaster on 2007-01-04
Can you post what this results in?

Copy and paste this into the terminal:

lspci | grep Broadcom\ Corporation

---

### Post by boilermaker on 2007-01-04
This was the output

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by MasterOfDisaster on 2007-01-04
This is a guide specific to your card, so try this first:
 
If using Dapper: [http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)
If using Edgy: [http://ubuntuforums.org/showthread.php?t=285809&highlight=howto+network+manager](http://ubuntuforums.org/showthread.php?t=285809&highlight=howto+network+manager)

Before following the Dapper guide, though, you need to have Network Manager installed (handy for Edgy too though):

sudo apt-get install network-manager-gnome

Then follow the applicable guide above, then follow on down below.

Check in System -> Preferences -> Sessions -> Startup Programs to make sure that nm-applet --sm-disable is listed.  If not, add it.  Log out, then back in, then click on the new applet in the upper right hand corner.  Make sure that 'Enable Wireless' is checked, and then click on your wireless network.  Input the WEP key and you are good to go!

Cheers

---

