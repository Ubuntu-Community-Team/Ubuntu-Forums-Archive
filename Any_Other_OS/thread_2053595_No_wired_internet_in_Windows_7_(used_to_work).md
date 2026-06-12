---
title: "No wired internet in Windows 7 (used to work)"
date: 2012-09-05
forum: Any Other OS
---

### Post by Erik1984 on 2012-09-05
Hi all,

Yes I know this is not a Windows forum but I think it's in the right subforum and you guys (and girls) just tend to know a lot about all systems :P 

I'm trying to fix wired internet on my parent's Windows 7 machine. It always used to work but since a few weeks it refuses to connect. The PC is connected by wire to a router and gets an IP adres dynamically. Strange thing is that the Windows network center says it is connected to the router but something is wrong with the router or our ISP connection. That would be weird because all other devices on the network still have internet. Of course I tried a Ubuntu Live CD and voila... internet. So it's not that the network card is broken. I think we can now say the problem is inside Windows 7.

This is what I have tried with no result so far:
- Resetting modem and router
- Ipconfig /release and /renew
- winsock reset
- Manually install latest drivers from Intel (the integrated ethernet card is an Intel).

There was some success with reverting to a previous restore point but the next reboot (and probably some nasty update) connecting to the internet fails again. Furthermore the old 'good' restore point was gone. I tried another restore point and that seemed to work. I changed update settings to 'always ask' but after a day or two (I don't know exactly, it's not my machine).. again no internet.

I suspect some update is the trouble maker. Of course I have tried to Google for solutions also and I see similar stories but none of those solutions worked (the winsock commands, installing new driver). Some suggest disabling _all_ updates after successful restore but I find that irresponsible. 

What more can I try?

---

### Post by Laiquendi on 2012-09-05
Try to cleanse the system, maybe it's affected by some virus, maybe just windows grew old and it has too many holes in its register/settings.

Maybe the wire is not in good condition?

---

### Post by Erik1984 on 2012-09-06
That's what I forgot to mention, we already replaced the wire. The wire can't be the problem as Ubuntu (I tried the Live CD, a nice showcase of Ubuntu for my parents ;) ) had no problem connecting to the internet through that same wire.

It's something in Windows that causes the problem :-k

---

### Post by Erik1984 on 2012-09-08
Follow up: Yesterday I restored again to a restore point from 24-8 (after that internet connection is up) and changed the update settings so permission is needed to install.

---

