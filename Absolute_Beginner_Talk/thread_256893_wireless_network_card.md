---
title: "wireless network card"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by kievlak on 2006-09-13
I have a compaq v5000 laptop. I got it to recognize the wireless card, and it see's the driver in the device manager just fine. I cant get it to connect to the internet. it say is in some loopback, and wont connect to the card even though its there. any suggestions?

---

### Post by jordanmthomas on 2006-09-13
Go to System --> Administration --> Networking
Does it show a wireless connection?  You may need to configure it here.
If not, what kind of card do you have?

---

### Post by kievlak on 2006-09-13
no it shows the wireless there and that it is active. but it in some "loopback" and I cant get it to connect to the internet. its a Broadcom 54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support (the card is listed correctly in the device manager)

---

### Post by jordanmthomas on 2006-09-13
Loopback is the connection your computer uses if it cannot find any others to use.
Chances are you don't have any native linux drivers for your card (someone care to verify?)
You may have better luck if you use ndiswrapper which will allow you to use windows drivers

Automatix will allow you to install a nice graphical interface to manage ndiswrapper.
[http://www.getautomatix.com](http://www.getautomatix.com)

If you don't want to use automatix, plenty of information on ndiswrapper is available.

---

### Post by kievlak on 2006-09-13
lol new problem. I got ndiswrapper on just fine. under the wireless properties I can see the network and someone elses, so its reciving just fine. but I still cant connect :(

---

### Post by pak33m on 2006-09-14
kievlak,

It sounds like your network settings are not configured.  I have an IBM T30 with a Belkin G wireless card and I made it work.  I got my start at it by reading the man pages for iwconfig & also inthe wireless section of the forum.  Here's a wee HOWTO for what I did for my wireless connection:

Step #1 Obtain your network settings

Obtain your ESSID, KEY (if applicable) & Access Point MAC address from your wireless interface (or whereever your wireless router is connected).

Step #2 Edit wireless.opts to configure your wireless connection settings

Go to the terminal
Type sudo gedit /etc/pcmcia/wireless.opts to configure your wireless connection.

Browse through the list of wireless connections to see if yours is there.  If so, uncomment (or remove the #) it & enter your network settings, particuliarly ESSID, KEY & Access Point MAC address(Note-Read the man pages on iwconfig to find out what the settings refer to by typing man iwconfig at the termainal).  Otherwise you can create your own connection from the example at the end of the page, but make sure you uncomment the # before your connection in order to enable the settings.

Save wireless.opts when finished.

Step #3 Edit interfaces to enable your wiresless connection
Go to the terminal
Type /etc/network/interfaces to disable all other interfaces, except for the loopback (or lo).  Comment (or insert a #) each interface listed other than your wireless connection, which should be wlan0 (for Broadcom)& the loopback (lo).

Enter your network settings particuliarly your ESSID, KEY & Access Point MAC address.

Save interfaces when finsihed.

Step #4 Verify your wireless connection
Restart your laptop to verify that your wireless connection is enabled at startup.  (Note-You may or may not have LEDs on your wireless card). 

If all else fails either search the wiki or pickup the O'Reily Linux Unwired book.  The book provided me with a ton of answers!

Good luck...

---

