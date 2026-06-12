---
title: "How can I get the smoothest possible install on a Macbook 7,1"
date: 2019-05-13
forum: Apple Hardware Users
---

### Post by ethicole on 2019-05-13
I've been messing around trying to get this old macbook usable for the kids. I tried installing Ubuntu 18.04 (single boot, mac os was corrupt) last night and I ran into some hiccups, predictably. Namely, problems with the graphics driver and problems with wi-fi. Some Google searching informed me that this is a well-covered topic, but as I'm a complete beginner I'm still having trouble wading through all these resources to find exactly what applies to me. Can anyone help me get this thing running? I'm open to trying a different version if I need to. Thanks in advance.

---

### Post by wildmanne39 on 2019-05-13
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by ethicole on 2019-05-13
Hi, if you feel like looking into it I performed the test from your wireless script

[http://paste.ubuntu.com/p/4QsVCkNhj6/](http://paste.ubuntu.com/p/4QsVCkNhj6/)

---

### Post by wildmanne39 on 2019-05-13
Please do:
```
sudo -H gedit /etc/modprobe.d/blacklist-bcm43.conf
```
then remove brcmsmac and bcma modules from the blacklist file, save, close, then reboot your computer and that should do it, those two modules should not be blacklisted by default in your system, is ubuntu installed on a hard drive or are you running it in a live session? The modules you need and the firmware are included in the kernel by default, however in some cases the ssb and the b43 modules need to be blacklisted but in your case they already are.

Thanks

---

### Post by ethicole on 2019-05-14
This fixed my problem, thanks!

---

