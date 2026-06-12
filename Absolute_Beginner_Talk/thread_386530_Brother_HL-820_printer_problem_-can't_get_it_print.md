---
title: "Brother HL-820 printer problem -can't get it printing"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by luki07 on 2007-03-17
Hi,
I've just installed Kubuntu and everything has gone fine, so far. Until I can't figure out how to set up my printer. I tried to add new printer using KDE-Printer (it is Brother type HL-820) using the default setting (a local printer directly connected to my pc, /dev/lp0, and cups --> default), and it is added to my printer list, but I can't get it worked.

I've tried re-installing cupsys, restart cupsys, but still no luck, so far. Looking at the user guide doesn't help that much either, as what I've done is basically the same.
Am I missing something here, like setting user permission to run cupsys, or something? Coz the model that I have is listed on the menu, so I figure it shouldn't be a driver problem. 

Please, any help would be appreciated.

Grrts

---

### Post by luki07 on 2007-03-20
Found solution. It seems a bug problem in (K)Ubuntu as Ubuntu fails to auto-detect the printer (although the model is on the list en surely linux compatible!!!) Other distros (Vectorlinux, PCLinuxOS) seem to detect it without any problem. Probably parallel-port detection bug or something. So, for the time being the only solution is moving to other distros. In my case, I've decided to move to Vector LInux. Great hardware detection (wireless, scanner, etc.), it uses KDE (I don't personally like Gnome), and it is amazingly faster than Kubuntu.

---

