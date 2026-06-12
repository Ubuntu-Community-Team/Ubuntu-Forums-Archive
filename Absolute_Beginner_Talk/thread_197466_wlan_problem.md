---
title: "wlan problem"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-15
The driver is installed with ndiswrapper for my wireless card, it says "driver present, hardware present".

What do I do now to activate it?

---

### Post by Sandlst on 2006-06-15
[QUOTE=WADemosthenes]The driver is installed with ndiswrapper for my wireless card, it says "driver present, hardware present".

What do I do now to activate it?[/QUOTE]
If your looking for a menu, goto (System/Administration/Networking)
If you are already doing this and see no wireless card, open a terminal (Applications/Accessories/Terminal) and copy/paste the following:```
sudo modprobe ndiswrapper
``` Also, just in case, are you in Dapper?  And if so, have you properly blacklisted the bcm43xx module (assuming you have a bcm43xx card)?
Post back if you have any problems.

---

### Post by WADemosthenes on 2006-06-15
[QUOTE=Sandlst]If your looking for a menu, goto (System/Administration/Networking)
If you are already doing this and see no wireless card, open a terminal (Applications/Accessories/Terminal) and copy/paste the following:```
sudo modprobe ndiswrapper
``` Also, just in case, are you in Dapper?  And if so, have you properly blacklisted the bcm43xx module (assuming you have a bcm43xx card)?
Post back if you have any problems.[/QUOTE]

Networking says that wireless is not active.  "sudo modprobe ndiswrapper" doesn't change it.

I have the latest version of xubuntu (minimal ubunut system running with XFce)

---

### Post by Sandlst on 2006-06-15
[QUOTE=WADemosthenes]Networking says that wireless is not active.  "sudo modprobe ndiswrapper" doesn't change it.

I have the latest version of xubuntu (minimal ubunut system running with XFce)[/QUOTE]
What happens if, in the 'Network Settings' menu, you right click the 'Wireless Interface', select properties, check 'Enable this connection' Select your wireless router from the pulldown 'Network name (ESSID):' set your WEP key if you have one, and set the 'Configuration:' to either DHCP or Static as you have it set up (probably DHCP if you dont know) click OK, then click 'Activate' with the Wireless Connection highlighted?  If this doesnt work, open a terminal and type ```
dmesg
``` and post the last dozen lines or so in here.  Post back if you have any problems.

---

### Post by WADemosthenes on 2006-06-15
[QUOTE=Sandlst]What happens if, in the 'Network Settings' menu, you right click the 'Wireless Interface', select properties, check 'Enable this connection' Select your wireless router from the pulldown 'Network name (ESSID):' set your WEP key if you have one, and set the 'Configuration:' to either DHCP or Static as you have it set up (probably DHCP if you dont know) click OK, then click 'Activate' with the Wireless Connection highlighted?  If this doesnt work, open a terminal and type ```
dmesg
``` and post the last dozen lines or so in here.  Post back if you have any problems.[/QUOTE]

Hey, thanks.  It worked perfectly without having to do "dmesg".

Except the lights aren't going off on the card... It's working but it doesn't look it from looking at the card.  Should I be worried or should I just go with it?

---

