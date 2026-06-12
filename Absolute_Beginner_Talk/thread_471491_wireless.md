---
title: "wireless"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by bjaurelio on 2007-06-12
my use of linux is limited. however, i did at one time have centos on my laptop and was able to get wireless to work using ndiswrapper, but i'm not sure if it was wpa or wep encryption. right now i'm using my sister's laptop b/c i can't get the wireless working on mine which i need to access the internet.

as the title indicates, my trouble is with getting wpa to work on my laptop. i'm using a sager 5680 with a dell truemobile 1300 minipci card i bought off ebay (broadcom bcm4306 rev 02). here are steps i've taken

installed ubuntu 7.04
installed the 3 packages for ndiswrapper (common, utils, and the gui) that i downloaded on this computer and copied to mine.
unzipped latest dell driver
installed using the graphical interface, to which is says "Hardware present: No"
tried using network manager to configure, but it only has option for wpa, only 2 wep options

found something on a webpage about blacklisting default bcm43xxx driver 
uninstalled driver and entered that command into the terminal to blacklist that driver
reinstalled driver
no luck

downloaded wpa_supplicant package on sister's laptop
copied to my laptop
said already had the package, but chose to reinstall
no luck

tried using iwconfig and wpa_passphrase but no luck.

just realized if under network it is in roaming mode can left click on network icon and select 'connect to other wireless network' which allows for wpa.
entered the info for my network
no luck.

i'm thinking that because under wireless network drivers it says "hardware present: no" that it's something wrong with ndiswrapper or the driver, but i'm at a loss. any help would be much appreciated.

thanks

i just found out if i enable roaming mode that i can then left click the icon and choose connect to other wireless network. it allowed for wpa, but i'm not able to get a connection.

---

### Post by ajmorris on 2007-06-12
which kernel version are you using?

---

### Post by bjaurelio on 2007-06-12
2.6.20 - the kernel version on feisty

---

### Post by Seisen on 2007-06-12
Does it say anything about the driver?

---

### Post by bjaurelio on 2007-06-12
what do you mean does it say anything about the driver? where?

---

### Post by bjaurelio on 2007-06-12
if you're asking what files the driver comes from, it's bcmwl5.inf and bcmwl5.sys

---

