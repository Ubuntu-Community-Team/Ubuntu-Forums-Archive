---
title: "Install on Dell Vostro 1400"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2008-01-01
Here is my situation.
I just got a new laptop, a Dell Vostro 1400. I wouldn't consider myself a newb to Ubuntu, I am pretty familiar with the command line, but I have never tried Ubuntu on a laptop before. Now, as I am using this machine for school it is mission critical, but I would still like to have Ubuntu on it for security reasons. Due to this i have a couple requirements.
[LIST=1]
[*]Must Dualboot with XP
[*]Dell MediaDirect must remain intact
[*]WiFi is an absolute must.
[*]Hibernation is something I would love to get working, but not a deal breaker.
[*]Would like to have /home on a separate partition
[*]Would like a partition to put shared files in for both OSes
[/LIST]
I have already tried Wubi. Ubuntu installs in Wubi but X fails to start on reboot, I can't even get to a console to try and fix it. The error is something about bcmXXX-microcode.fw not working or something similar. 

I am very cautious with this machine because I plan to use it for school and I can't afford not to have it working. Any help would be appreciated on this situation.

```
System Info:
Windows XP Home Preinstalled
Dell MediaDirect 3 Preinstalled
1.4 GHz Intel Core 2 Duo Processor
Mobile Intel 965 Express GFX Card
14.1 in 1280x800 Screen
Dell Wireless 1390 WLAN Mini-card WiFi (I believe is a broadcom firmware card)
1 GB Ram
```

---

### Post by metallicatony on 2008-01-02
Mine too is Vostro 1400. Even i had the same problem..

Please download [http://ubuntuforums.org/attachment.php?attachmentid=48087&d=1193544558](http://ubuntuforums.org/attachment.php?attachmentid=48087&d=1193544558)

tar -xf bcm4318*.tar.gz
sudo ./ndiswrapper_setup
Use the internet (you will have to open the System menu at the top of the screen, go to Administration, and then click Networking. Configure the interface eth1 or wlan0, and connect to your wifi network)

If you need an extensive tutorial please have a look at [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by Nekiruhs on 2008-01-03
Bump? Does anyone know if this is doable even?

---

