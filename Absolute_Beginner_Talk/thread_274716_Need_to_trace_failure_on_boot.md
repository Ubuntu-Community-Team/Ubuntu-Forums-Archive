---
title: "Need to trace failure on boot"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by arran on 2006-10-10
Hi,

Can anyone tell me which logs or config files hold drivers or services started on boot?

My system runs very slow (50 seconds + to open teminal) and HAL fails to inialise. 

The LiveCD works great as does booting into recovery and only starting dbus, HAL and GDM.

--------------
Please be patient as I'm a Linux Newbie, aging Windows Techy
--------------
Clean install of 6.06 lts on 1st partition.
Centrino 1.6 laptop, 1 GB RAM, 
100GB ( 20G root primary, 25G WinXP primary, 2G swap logical, 50G)
Wireless disabled in bios

---

### Post by lkagan on 2006-10-10
I've had a similar issue. I never really got down to the bottom of it but I did figure a hack around it.  You probably have a samba mount setup in /etc/fstab.  If you disable the mount at boot (mount it later), then the system won't hang.  I hope this is the case so that you can quickly move on. If the samba mount is the issue and you find a 'real' solution, please post it back for the rest of us.

Hope this helps

Larry Kagan

---

### Post by arran on 2006-10-10
Thanks Larry,

Having trawled the forum that was one of the first things I looked for.

Ta anyway

---

