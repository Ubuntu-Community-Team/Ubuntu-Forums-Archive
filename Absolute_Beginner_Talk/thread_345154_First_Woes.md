---
title: "First Woes"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by deadowl on 2007-01-23
Okay, so my problems with trying to switch from XP to Ubuntu on my Dell D820 Notebook:
[COLOR="SlateGray"]
1. Screen Resolution: natural resolution of 1680x1050, but Screen Resolution Preferences are offering me 1280x1024, 1024x768, 800x600, and 640x480. (resolved :))
[/COLOR]
2. WLAN: I can't connect to it. [COLOR="SlateGray"]I would also need Cisco's VPN Client to connect to my school's network.[/COLOR]

I have tried installing Ubuntu on many other computers, and these two problems have been persistently occurring. I would like to convince other's to use Ubuntu, but I can't unless I know how to address these two problems correctly and safely.

Computer: Refurbished Dell Latitude D820

1. Intel Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

2. Broadcom Corporation BCM4310 UART (next step down the tree in the Device Manager, WLAN Interface is unknown)

If someone could help me, I'd be grateful.

---

### Post by sardion on 2007-01-23
To deal with the screen resolution you need 915resolution.  It's in the repos.  I don't know how it works, but it will do the job.

As to VPN, getting Cisco's to compile on newer kernels is a real hassle.  My school's network was fine with me using vpnc which is a clone of Cisco's client that also happens to be in the ubuntu repos.  I say try using vpnc and see if it works, it usually does.

As to wireless, I personally dont know anything about that card, etc.  Repost your question with a subject indicating the wireless is the problem and with the card name.  Someone will know and will help you out.

---

### Post by Bachstelze on 2007-01-23
1. You might want to have a try at *915resolution*. I can't tell you how to use it but I know it's the tool used to get correct resolution on Intel graphic chips.

2. Broadcom has basically gived the Open Source community the middle-finger  and has not released the specs of their hardware, nor Linux drivers for it. But you can use [Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28Ndiswrapper%29) to use the Windows drivers in Linux. Can't help you with VPN, sorry.

---

### Post by deadowl on 2007-01-24
Okay, so I have fixed my screen resolution, and VPN now works.
However, I tried using ndiswrapper, and it seems to have taken me a step backwards because now wireless isn't even network settings. :(

---

### Post by hscottyh on 2007-01-24
With ndiswrapper you have to install the correct firmware (packaged with the windows driver) for you card. I find an easy way to do this is use the GUI program ndisgtk. You'll have to install it.... 

sudo apt-get install ndisgtk

You should be able to get the correct wireless windows drivers from dell. If its on exe or a zip you get from dell you'll have to extract the files. either cabextract or unzip should should extract the files depending on how they were packaged.

Then use run ndisgtk and select the .inf file. This should properly install the firmware. If it say's detected you most likely are in luck. If not you'll have to find a more compatable windows driver. Anyone remember the url that has the links to drivers listed by chipset/manufacter?

---

### Post by Jan Hrbacek on 2007-02-05
[http://www.ubuntuforums.org/showthread.php?t=301527&highlight=D820](http://www.ubuntuforums.org/showthread.php?t=301527&highlight=D820)

---

### Post by sailor2001 on 2007-02-05
> **hscottyh said:**
> With ndiswrapper you have to install the correct firmware (packaged with the windows driver) for you card. I find an easy way to do this is use the GUI program ndisgtk. You'll have to install it.... 

sudo apt-get install ndisgtk

You should be able to get the correct wireless windows drivers from dell. If its on exe or a zip you get from dell you'll have to extract the files. either cabextract or unzip should should extract the files depending on how they were packaged.

Then use run ndisgtk and select the .inf file. This should properly install the firmware. If it say's detected you most likely are in luck. If not you'll have to find a more compatable windows driver. Anyone remember the url that has the links to drivers listed by chipset/manufacter?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Listindex.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Listindex.php/List)

---

### Post by deadowl on 2007-02-05
Yea, i figured that out a while ago. One strange thing though, I can only have one connection (wireless/wired) enabled or nothing will work. 

Also, any advice/good applet for detecting/switching wireless SSIDs? I don't have to use it here at school since I'm only looking for one SSID, but when I get home and go around visiting friends, it would probably be a good thing to know about

---

