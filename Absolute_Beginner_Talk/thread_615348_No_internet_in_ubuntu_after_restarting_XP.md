---
title: "No internet in ubuntu after restarting XP"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Popz on 2007-11-17
Hi, I have recently upgraded to Ubuntu 7.10 and I'm getting a problem with my Ethernet connection. Every time I boot Windows XP (I'm doing a dual boot) and restart to boot into Ubuntu my Ethernet stops working (it still works if i reboot into windows though). The light on my router that indicates if a connection is detected between my computer and router is blank. It lights up when i reboot into windows however, and turns off when i reboot into Ubuntu. The only way I can get internet back into Ubuntu is if i shutdown my computer and boot into Ubuntu without restarting from windows. And i can restart and reboot into Ubuntu and it will still work. Any ideas on what I can do so that I can reboot from Windows to Ubuntu and still have an internet connection without having to turn off and back on again.
Thanks.

---

### Post by uclalinux on 2007-11-17
I had a similar problem, I don't remember the exact solution, but I had to find what module  i needed and remove all the other Ethernet modules and then make sure that during my linux boot that my rc sript included the correct module to load.

---

### Post by fourscore on 2007-11-17
Are u having  Realtek Ethernet card,  If so then pls refer to the flwg link - [http://ubuntuforums.org/showthread.php?p=3446114](http://ubuntuforums.org/showthread.php?p=3446114)

---

### Post by Popz on 2007-11-17
Yes it worked thanks fourscore

---

