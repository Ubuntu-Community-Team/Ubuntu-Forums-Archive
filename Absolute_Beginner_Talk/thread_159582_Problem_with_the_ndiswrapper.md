---
title: "Problem with the ndiswrapper"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-13
I have finally managed to install it, through synaptics, and got it to recognize the windows driver.

It detects when my wireless card is connected, but then I press the "configure networks" button, it brings me to the networking screen, and my card is not there, only Ethernet and Modem. 

Is there anything else that needs to be done and I've missed?

thanks,
Josh:)

---

### Post by taurus on 2006-04-13
[QUOTE=Caligula]
Is there anything else that needs to be done and I've missed?

thanks,
Josh:)[/QUOTE]
Yes, you can list the name of your card and how you installed the driver (which version) for it using ndiswrapper!

---

### Post by Goonie on 2006-04-13
Hi is the card listed if you do *ifconfig* in terminal? If so what happens if you do *ifconfig adaptername up* ?

I had real problems with ndiswrapper in breezy the other day, got as far as you and then managed to get the card listed in the networking setup window in Gnome but when I tried to activate it from there my machine frose completely and I couldn't boot up again because I got a kernel panic error. I had to boot up from an older kernel and remove the ndiswrapper entry in /etc/modules .

Goonie

---

### Post by Caligula on 2006-04-13
It is a D-Link DWL-G122 USB card. I installed the .inf file from the CD I got with it.

It doesn't appear if i type ifconfig...

---

### Post by dabear on 2006-04-13
[QUOTE=Caligula]It is a D-Link DWL-G122 USB card. I installed the .inf file from the CD I got with it.

It doesn't appear if i type ifconfig...[/QUOTE]
You have to bring in the ndiswrapper module. You can do that  temporary with «sudo modprobe ndiswrapper», but if you want a permanent solution(from next reboot), you'd have to write «sudo ndiswrapper -m»

---

### Post by taurus on 2006-04-13
[QUOTE=dabear]You have to bring in the ndiswrapper module. You can do that  temporary with «sudo modprobe ndiswrapper», but if you want a permanent solution(from next reboot), you'd have to write «sudo ndiswrapper -m»[/QUOTE]
And if you want to run "modprobe diswrapper" everytime you boot without typing it in, add it to /etc/modules!

---

### Post by dabear on 2006-04-13
[QUOTE=taurus]And if you want to run "modprobe diswrapper" everytime you boot without typing it in, add it to /etc/modules![/QUOTE]
Please do read the last part of my post again.
> 
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
**-m                Write configuration for modprobe**



---

### Post by zerhacke on 2006-04-13
Dabear, ndiswrapper -m is SUPPOSED to write to /etc/modules, but in my experience most of the time it just says it wrote it and does not.

Most cards, you have to add```
ndiswrapper
```manually to the end of /etc/modules.

---

### Post by taurus on 2006-04-13
[QUOTE=dabear]Please do read the last part of my post again.[/QUOTE]
Well, excuse me then...

---

