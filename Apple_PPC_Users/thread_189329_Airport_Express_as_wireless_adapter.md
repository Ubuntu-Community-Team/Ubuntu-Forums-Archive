---
title: "Airport Express as wireless adapter"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by musik2liv on 2006-06-05
So I am currently running a brand new install of latest Ubuntu (6.06 I believe), from auto update.  It's running all alone on my iBook G4, 1.2 GHz.  I have an airport extreme card installed, but during all my research for solutions, it all seems to point to the workaround for the card that requires having Mac OS X installed as well.  I have an airport express which I no longer use for anything. (purchased the Roku Labs music bridge)  I am curious if there would be any issues with using this as a semi-wireless solution for my iBook since I want to move it to my office rather than being tethered to my bedroom where my airport extreme base station and modem reside.  It seems maybe I will have to set it up from my one of my other computers (WDS and whatnot) and just plug it in and go?  Any ideas are greatly appreciated.  If anyone needs more info on equipment let me know as well, I will gladly provide.

---

### Post by dombleu on 2006-06-05
You don't NEED osx installed. But it helps, just to get the firmware file for the wireless card. But you can have it from anyone who got osx installed. Like me! :)

---

### Post by musik2liv on 2006-06-06
[QUOTE=dombleu]You don't NEED osx installed. But it helps, just to get the firmware file for the wireless card. But you can have it from anyone who got osx installed. Like me! :)[/QUOTE]
So do you mean I can follow the directions for "extracting" the firmware file on one of my other macs running OS X and then just transfer that to my iBook?  I suppose I never thought of it that way.  You have it successfully working this way on your powerbook?  If so, that would be perfect.  It kills me to have a laptop tied down like it is right now.

---

### Post by benoitc on 2006-06-06
[QUOTE=musik2liv]So do you mean I can follow the directions for "extracting" the firmware file on one of my other macs running OS X and then just transfer that to my iBook?  I suppose I never thought of it that way.  You have it successfully working this way on your powerbook?  If so, that would be perfect.  It kills me to have a laptop tied down like it is right now.[/QUOTE]


Airport extreme works on my powerbook5,6 too (02/2005) too. But not without pain. And reception isn't very good. I test it in many location last week (street of paris, meeting, @ home ..) and have some deconnexion or loss of signals. More over having to relaunch the connexion is only possible by unloading/reloading the kernel. And with some dhcp server, it seems impossible to get an ip automatically witch is reaally annoying. Didnt work thouth with my ABS (last firmware). More over connexion don't come back from sleep.

Steps to do each time to launch connexion (don't works automatically), I use AppleAirport2 firmware:
```

sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 channel <CHANNEL>
sudo iwconfig eth1 enc <MYKEY>
sudo iwconfig eth1 essid <MYESSID>

```


For now I think wifi connexion with airport extrem is a pain on linux. Tis isn't integrated in ubutu as it is in osx.

---

