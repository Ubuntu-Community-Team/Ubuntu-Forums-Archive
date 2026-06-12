---
title: "Macbook Core 2 Duo + Gutsy + Madwif = Nope!"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by rickwood on 2007-10-20
Just downloaded Gutsy and it looks and works great.  However I haven't been able to get the wireless to work yet.  I followed the instructions in the Macbook wiki to install Madwifi drivers.  This appeared to work, as I can now see all of the wireless networks in my neighborhood, including my two wireless networks.

The problem is that although I can see the wireless networks, I can't connect to any of them.  I even unprotected my network to see if this was the problem.  Nope -- still counldn't connect.

I searched the madwifi site, and tried a few suggestions I found there like disabling eth0 and adding ath_hal to the disabled modules list.  These didn't help.

I found another suggestion to try an older version of Madwifi from August of this year that people were having good luck with, but this acted the same as the latest drivers.

I don't have mac address filtering turned on in my router, so that's not the problem.

I'm stumped as to what to try.  The version of Ubuntu 7.10 I installed is the amd64 version, and I used the alternate install cd.  If I understand correctly, my choice of amd64 prevents me from trying ndiswrapper.

And ideas out there?  Is it possible that the i386 version would have better luck in regard to wireless on a Macbook Core 2 Duo?

---

### Post by mert on 2007-10-20
FWIW, I just installed Gutsy x86 and then followed the directions to install madwifi-latest.  I rebooted and connected to my wifi no problem.  I'm using a WEP/ascii passphrase (need to change that...).

---

### Post by cyberdork33 on 2007-10-20
> **rickwood said:**
>  I'm stumped as to what to try.  The version of Ubuntu 7.10 I installed is the amd64 version, and I used the alternate install cd.  If I understand correctly, my choice of amd64 prevents me from trying ndiswrapper.
You can use ndiswrapper, you just have to find a 64-bit windows driver for your chipset.

---

### Post by mert on 2007-10-20
Correction: It works until I try to start bittorrent or azureus, then I lose my connection altogether.  I don't think its my router because I can reboot my laptop and it automatically connects again.  Also, when I use Mac OS I don't have this problem.  I can try to load a driver using ndiswrapper but first I have to figure out how to uninstall the madwifi driver.

---

### Post by rickwood on 2007-10-20
Uninstalling MadWifi is pretty easy.  In a terminal, go into the madwifi directory (where you unzipped the file and compiled it).  From there, type

```
make uninstall
```

That's it.  If you already deleted the madwifi directory, you can simply re-download it and unzip it again, then issue the make uninstall command as stated above.

---

### Post by rickwood on 2007-10-20
> **cyberdork33 said:**
> You can use ndiswrapper, you just have to find a 64-bit windows driver for your chipset.

Anyone know if such a driver exists for a core 2 duo macbook?

---

### Post by hackworth on 2007-10-20
according to this ticket, it looks like an older version of the driver might work better:
[http://madwifi.org/ticket/1543](http://madwifi.org/ticket/1543)

---

### Post by rickwood on 2007-10-21
Tried several older versions of madwifi with no luck.  Gave up and installed i386 version of ubuntu over amd64 version.  Tried madwifi with this setup - same results - could see the networks, but couldn't connect.  Uninstalled madwifi, installed ndiswrapper with atheros driver from BootCamp.  Works great!  Now if I could just find an updated Windows driver that supports wireless N and install it using ndiswrapper, all would be perfect (not sure if an updated version of BootCamp has a wireless N Windows driver or not)!

---

### Post by cyberdork33 on 2007-10-21
> **rickwood said:**
> Tried several older versions of madwifi with no luck.  Gave up and installed i386 version of ubuntu over amd64 version.  Tried madwifi with this setup - same results - could see the networks, but couldn't connect.  Uninstalled madwifi, installed ndiswrapper with atheros driver from BootCamp.  Works great!  Now if I could just find an updated Windows driver that supports wireless N and install it using ndiswrapper, all would be perfect (not sure if an updated version of BootCamp has a wireless N Windows driver or not)!

I don't know that it is possible to get n connections with ndiswrapper at the moment. The Apple drivers should support 802.11n.

---

### Post by rickwood on 2007-10-22
After a little use, I've found another problem.  When waking the macbook from a sleep, the network is hit and miss.  Sometimes it comes back just fine, and other times it's dead.  In these instances, network manager also seems to be unresponsive.  Any idea what the best way is to restart the network and network manager in these situations?

---

### Post by cyberdork33 on 2007-10-22
> **rickwood said:**
> After a little use, I've found another problem.  When waking the macbook from a sleep, the network is hit and miss.  Sometimes it comes back just fine, and other times it's dead.  In these instances, network manager also seems to be unresponsive.  Any idea what the best way is to restart the network and network manager in these situations?

You can try:
```
sudo /etc/init.d/networking restart
```

---

### Post by mcdull2k on 2007-10-23
make sure that you have to stay very close with the router.. the range is with huge different from using windows and mac driver.

---

### Post by Ghola28 on 2007-11-11
rickwood: I had the same problem with the same setup (64-bit version of Gutsy on C2D Macbook).  Fixed it last night by first installing the latest madwifi drivers (per the directions in the MacBook Ubuntu install doc) and then following the manual directions on the MadWifi Newbie HowTo site: 
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

I've attached a shell script I wrote that runs the commands needed to setup your wifi for a non-password-protected network.  Just replace KR1 in the second-to-last command with the name of your network (from apscan.txt).  

If you haven't used a shell script before, just save the file to your home folder and rename it (leave off the .txt from the name).  From a terminal, type "chmod +x *filename*" where *filename* is the name of the script file.  Then you should be able to type "./*filename*" to run the script.

Hope it works for you.

---

### Post by rickwood on 2007-11-12
Ghola28,

This weekend I managed to get the latest madwifi driver working on a 32-bit install (didn't do anything fancy, just tried the latest version).  It will connect to my wireless-G WEP encrypted network just fine.  But it still doesn't like my wireless-N WPA enrcypted network for some reason.

Next weekend I plan to switch back to the 64-bit Gutsy, and will give your script a try.  I may also try and use it as a starting point for a new script to run when coming out of suspend (i.e., the network has been hit and miss when coming out of suspend, and I need an easy way to restart it when it doesn't work after suspend).

Thanks!

---

### Post by Ghola28 on 2007-11-14
Improved script: (run the commands in the old script from the terminal to setup your wireless first, use this to connect after reboot/wake from suspend)

#!/bin/sh

iwconfig ath0 essid "KR1"
dhclient ath0

Call it something like "wifihelp.sh" and give it executable permissions.  Run it from the terminal with: sudo ./wifihelp.sh

This worked for me.  Not quite as convenient as the Network Tools, but a small price to pay for 64-bit.

---

