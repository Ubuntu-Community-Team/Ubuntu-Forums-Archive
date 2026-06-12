---
title: "wireless setup for server install, HELP!!!"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-16
so, i screwed something up so badly, i've had to reinstall. i've decided to go with a server install, using openbox. everything is cool, except that i can't figure out my wireless. it's a linksys wusb11 v.2.6 (802.11b). when i did a full install, all i had to do was open up 'network-admin', enter the essid and press activate and i was up and running. right now, the green light on the device is lit. when i enter *iwconfig*, i get...

[i]lo   no wireless extensions

wlan0   IEEE 802.11-DS  ESSID:"okuwlan"  Nickname: "okuwlan"
and a bunch of other stuff...[/i]

what do i do?

---

### Post by romdos on 2006-02-17
if you have an open wireless network that serves up dhcp, all you need to do is type into a terminal:

  sudo dhclient wlan0

and you should get a dynamically configured ip address


if you have a wep key you will need to do something like this before dhclient:

  sudo iwconfig wlan0 key (your key in hex)

if you use a different channel than the default:

  sudo iwconfig wlan0 channel (your channel #)

you can combine in one line: 

  sudo iwconfig wlan0 key (your key in hex) channel (your channel #)

you may need to do other stuff as well depending on your access point.

Check out iwconfig's man page for all the cool stuff you can do with it

---

### Post by fuscia on 2006-02-17
thanks for the help.

---

