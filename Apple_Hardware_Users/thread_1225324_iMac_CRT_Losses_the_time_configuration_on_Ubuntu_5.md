---
title: "iMac CRT Losses the time configuration on Ubuntu 5.04"
date: 2009-07-28
forum: Apple Hardware Users
---

### Post by Genyns on 2009-07-28
Hello guys, this is my first time posting in the forums, and it's because I'm desperate I can't find any solution for the problems I'm having.
 
I have installed ubuntu 5.04 ppc on my wife's iMac CRT, (because any other distro will not pass a blank screen on booting from CD) formely it had installed MAC OS 9.2. The installation was successful but it losses the hour configuration everytime I unplug it, and we I try to log in two error windows pop-up:
 
1. An error has ocurred when the Daemon of Gnome Preferences Administrator tryied to start.
Some things like themes configuration, sounds of wallpapers would not work properly.
The Gnome Preferences Administrator has been restarted too many times.
Gnome will keep trying restart the Preferences Administrator the next time you log in.
 
2. A problem has ocurred when registering the panel with the bonobo-activation server
Error code 3
the panel will finish now.
 
If I close both errors the desktop will load without the wallpaper and clock panel, when I check the date/clock conf tool it is set on 31/12/1903 0:00:00.
If I reconfigure it (a error when I click OK "Failed to run time-admin, son process finished with the state 251" but It configures it properly somehow) and when restart I can get to the desktop without errors.
I though It has something to do with the iMac battery and open the bottom I tested the battery and it has no charge I recharged it and put it in again, I reconfigured the clock and left the iMac unplugged the whole night, in the morning I plugged it back and the error appeared again, I think it has something to do with the hardware clock because when the system is booting this line appears "setting the system clock using the hardware clock as reference" I have no Idea how to change the iMac hardware clock. 
 
Please help if someone know a way to fix my problem :confused:
 
PD. Sorry my english is bad.

---

### Post by rjcalifornia on 2009-07-28
Look, the small battery that is inside the imac must be dead. You should access Mac OS first, change the time and DATE, restart, then boot Linux.

The error happens because of the DATE changes to something in the 70's

---

### Post by Genyns on 2009-07-28
Unfortunately I used the complete disk to install ubuntu, so there is no mac os to boot. Thanks for the reply I'll check the battery again.

---

### Post by 3rdalbum on 2009-07-29
> **Genyns said:**
> Unfortunately I used the complete disk to install ubuntu, so there is no mac os to boot. Thanks for the reply I'll check the battery again.

Replace it, don't recharge it.

The time problem is causing the other two errors - it's a bug specific to those early versions of Ubuntu. You'll probably find that later versions of Ubuntu (more specifically, Xubuntu) are much much better on your iMac, assuming it has enough memory.

---

### Post by Genyns on 2009-07-29
Thanks for the reply I'll try to find a replacement for the battery, also thanks for the suggestion of xubuntu, i'll try it. I had some problems trying to install ubuntu 8.10 for ppc, it gets stuck on a blank screen when tryin to boot from the installation CD, I hope Xubuntu 9.04 version doesn't have this problem.:)

---

### Post by Genyns on 2009-07-30
I tried to install Xubuntu 9.04 on my iMac CRT G3, but happens the same blank screen and the iMac shuts down automatically when trying to boot from CD-Rom only ubuntu 5.04 could be installed successfully, but I still have the problems above.

---

