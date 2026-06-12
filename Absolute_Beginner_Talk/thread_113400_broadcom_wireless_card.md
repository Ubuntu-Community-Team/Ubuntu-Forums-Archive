---
title: "broadcom wireless card"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by new_to_ubuntu on 2006-01-06
I get an error, I researched it and all roads point to one module has overwritten the other I need to remove the offending module. How do I do this.

Ubuntu sees my wireless card, tried installing drivers with ndiswrapper...this is where the error comes in. something like error inserting.....

M

---

### Post by Mr. Electric Wizard on 2006-01-06
It's not a USB card is it?

This is the HowTo I used to get my Broadcom wifi card to work...
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom")

The one step that shows **"sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile" **  I didn't have to do because this line was not in the .conf

After I did that, i installed GTKWifi (1.09) and all was working exactly right.
Good luck

---

### Post by new_to_ubuntu on 2006-01-07
Wireless card is onboard. Not a usb or pcmcia card. Tried the how to, wireless light is on. Can't see it in System/Admin/Networking. Ethe0 and modem are the only listings. 

???

M

---

