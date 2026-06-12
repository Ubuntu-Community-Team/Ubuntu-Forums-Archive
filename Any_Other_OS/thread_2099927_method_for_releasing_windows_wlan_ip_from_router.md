---
title: "method for releasing windows wlan ip from router"
date: 2012-12-31
forum: Any Other OS
---

### Post by robertthebruce on 2012-12-31
hi all and a happy new year...

ive misplaced the method for releasing windows wireless card ip from itself and a router...

im really hoping this is how to describe it, as i cant refind it

---

### Post by Gogsyd on 2012-12-31
Just to clarify are you wanting to do this from a windows PC?
If so there are two ways:
Cmd prompt and type ipconfig /renew

Or

Right click the adaptor in your network options and there is an option there. Can't remember the name as I'm not in front of a PC. 

Not sure if that's what you were after. Hope it helps

---

### Post by howefield on 2012-12-31
Thread moved to the "Other OS/Distro Talk" forum.

---

### Post by robertthebruce on 2012-12-31
your right Howefield, had i been able to work out which forum to post it in i prolly would have relised to to ipconfig --help windows...

many thanks Gogsyd, you jogged meinto it

ipconfig /release



02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by Gogsyd on 2012-12-31
Glad it helped.  ipconfig /renew actually releases then renews it however I tend to do /release first and then /renew as it seems to work better.

Happy New Year (for tomorrow)

---

