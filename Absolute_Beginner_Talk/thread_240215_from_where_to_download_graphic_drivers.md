---
title: "from where to download graphic drivers"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2006-08-20
hi 2 all

is their any way by which i can know what graphic drivers are required by my machine. 
i have intel 865 chipset (on desktop) and 915gm chipset (on laptop) 
previously desktop was using i810 drivers which are natively provided by the default installation on ubuntu. itworked well but while playing games like Age of empires it really slow down the machine. so i decided to get the latest drivers from the intel site. while compiling their was some error so i just quited and shutdown. but when i restarted xserver crashed with some errors whe n i checked the xorg.conf it said ATI Radeon instead of intel.  plz help. how do i reconfigure xserver.? and plz suggets some drivers for both my laptop and desktop.

---

### Post by catlett on 2006-08-20
The command for reconfiguring your xserver is ```
sudo dpkg-reconfigure xserver-xorg
``` You can most likely select the defaults. This should get you back in x but it won't give you any special drivers. Sorry I do not know about intel drivers.

---

### Post by anurag_gupta on 2006-08-21
thanx itgot me backintoX. but still while playing AOE the graphics cause the system to slow-down.   i'm using cedega to play AOE.

---

### Post by az on 2006-08-21
> **anurag_gupta said:**
>    i'm using cedega to play AOE.
That's the issue.

The Xorg drivers are relatively new, so that's not the problem.

---

### Post by anurag_gupta on 2006-08-21
but while playing AOE thru wine graphics get even worse and their is no sound output

---

