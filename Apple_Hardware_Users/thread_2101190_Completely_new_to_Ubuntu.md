---
title: "Completely new to Ubuntu"
date: 2013-01-04
forum: Apple Hardware Users
---

### Post by AirunJae on 2013-01-04
So I am completely new to Ubuntu and am interested in installing/dual-booting it on my MacBook Pro. It is a 2008 model (4,1) and I have updated the RAM from 2 to 4 GB.

I have tried installing rEFIt, but it does not come upon restarting the system. The other issue I have is that the HD does not want to repartition either. When I click on Storage, it says I have 91.88 GB available. However, clicking under Disk Utility it says I only have 16.8 GB available. Any suggestions would be greatly appreciated.

Thanks!

---

### Post by powerpcliberation on 2013-01-04
The best and most thorough method would be to backup Mac OS with TimeMachine first.  After this boot from the Mac OS DVD and partition the drive the way you want.  Then restore Mac OS followed by installing Linux.  

OS X and Linux don't live happily together on the same drive generally so you should consider 3 partitions.  Mac OS/Linux/Shared Space.  Put all your media and documents on the Shared space partition.

For networking Linux with Mac OS devices use "Netatalk".

Hope that helps.

EDIT:

I just thought of another more simple and direct solution that will bring far less headaches.  You could boot the lesser used of the two OS from a high speed thumb drive.

---

### Post by Rocklobster690 on 2013-01-05
If you are completely new to Ubuntu I wouldn't recommend duel booting yet. 

Instead use VirtualBox to run x64 instance whilst you explore what's on offer.

---

