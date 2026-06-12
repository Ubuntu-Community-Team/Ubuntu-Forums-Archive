---
title: "Ethernet not obtaining IP Address"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by stuart264 on 2008-01-15
Guys (and Guy-ette's)

I have a problem, right before I went away on the 27th November I downloaded the latest updates and restarted my Linux drive, i came back home on the 6th January booted my machine and the Ethernet adaptor says its connected to the Router but the connection light on the router fails to light and it  does not obtain an IP address on DHCP but the hardware is fine as it runs perfectly on Windows.

Any suggestions?

---

### Post by Law506 on 2008-01-15
If it worked before, then this might not be the right resolution, but is your network card in windows set to auto start on boot up?  Windows has a setting that disables the network card until the system is in windows, which would disable your card when you go into linux.  But as I said, if it worked before, this might not be the answer, but this is what was happening to me back in the day.

---

### Post by Het Irv on 2008-01-15
The same has happend to me before and to get it to work I had to unplug and replug my Cable modem.  I don't know why it worked but it did.

---

### Post by stchman on 2008-01-15
> **stuart264 said:**
> Guys (and Guy-ette's)

I have a problem, right before I went away on the 27th November I downloaded the latest updates and restarted my Linux drive, i came back home on the 6th January booted my machine and the Ethernet adaptor says its connected to the Router but the connection light on the router fails to light and it  does not obtain an IP address on DHCP but the hardware is fine as it runs perfectly on Windows.

Any suggestions?

You could restart network manager.  Also try what Het Irv said to power down the cable modem and router.  If you do, do it for at least 2 minutes.

```
sudo /etc/init.d/networking restart  
```

---

### Post by stuart264 on 2008-01-15
I will give those a try in the morning........quick response btw, I expected to post and read the replies in the morning

---

### Post by stuart264 on 2008-01-16
Neither of those things worked any other suggestions?

---

### Post by c0met on 2008-01-16
I don't always get a network connection when I first log in. When that happens, I right-click on the network icon (up near the log-out icon) and uncheck "Enable Networking". Then I right click on the icon again and put a checkmark to enable networking. This always works for me. I just that occasionally I have to kick start the network :)

---

### Post by stuart264 on 2008-01-16
nope tried that too, its almost like the update I did in November before I went away upgraded the ethernet drivers which didnt install right. 

Anyone know how to download and re-install them manually as it might be something to try

---

### Post by c0met on 2008-01-21
If you are still interested, I came across this thread and it might help,

[http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf]("http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf")

---

### Post by stuart264 on 2008-01-24
Finally found the problem, I needed to enable the "Wake on LAN" settings in my bios, no idea why it suddenly needs it but with this version of Ubuntu as it never needed it before but it obviously does.

Probably a bug in the network drivers that needs looking at by better heads than mine.

---

### Post by hyper_ch on 2008-01-24
how about switching to a static IP in your lan?

---

### Post by stuart264 on 2008-01-24
Already did months ago and changed the DNS to OpenDNS in my Linksys Router still cant figure out why the old version of 7.10 didnt need wake on lan enabled to connect but this version does. 

Must have something to do with the Realtek 8139 chipset because I noticed another post on here about a user having the same problem with a new laptop which gave me the idea to try enabling wake on lan and see if it worked and it did.

---

