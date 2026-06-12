---
title: "bluetooth mouse can't be found won't connect"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by TEDNUGNT on 2007-04-26
i am running 7.04 ubuntu on an ASUS w3v with dual-boot. under windows my kensington bluetooth mouse runs fine.

yesterday i followed the documentation i read on using the mouse with Ubuntu and it worked great.

today i cant get it to work.

could i have messed up the /etc/default/bluetooth file? i thought i made only the changes i was supposed to, ie. "hidd_enabled=0 to hidd_enabled=1"

i have tried restarting "sudo /etc/init.d/bluetooth restart" several times and then running "sudo hidd --search" to no avail. when i try to connect directly "sudo hidd --connect de:vi:ce:ad:re:ss"
it says "cant get device info: no route to hose". similarly "hcitool scan" nor "hcitool dev" yields no devices found.

help. thanks.

---

### Post by NICU on 2007-04-27
Hi, I'm not familiar with that mouse, but for most Bluetooth devices you have to set them to discovery mode at the same time you try to scan for them.  There's usually a sync button on the Bluetooth device that will put it into discovery mode for ~30 seconds and in that time you need to do your scan and go through the pairing process.  Let me know if that helps.

---

