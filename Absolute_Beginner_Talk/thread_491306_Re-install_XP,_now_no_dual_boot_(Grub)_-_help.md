---
title: "Re-install XP, now no dual boot (Grub) - help"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by OzzMosiz on 2007-07-03
ok I reinstalled WinXP on my machine. Now I am unable to dual boot. I've managed to get to a linux shell by booting from CD, but when I try and run the grub find, it comes back with nothing.

I'm now completely lost. I've read a few other threads that tackle similar issues, but none have helped :'(

---

### Post by vexorian on 2007-07-03
you have to reinstall grub to the MBR using the live cd.

as for the technical details, there are plenty of howtos: [http://www.google.com.bo/search?q=site%3Aubuntuforums.org+restore+GRUB&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.bo/search?q=site%3Aubuntuforums.org+restore+GRUB&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by manndani on 2007-07-03
You could try this. [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)  I haven't used it but it seems to get good reviews.

---

### Post by OzzMosiz on 2007-07-03
Just tried supergrub, burnt to CD and it doesn't boot off of it (my bios is set to boot from CD first).

---

### Post by Raineer on 2007-07-03
Use your Ubuntu Live CD and follow [this]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot"). It says Vista but works fine for XP. I did exactly the same thing and this works great.

---

### Post by OzzMosiz on 2007-07-03
Rainer, that was a new one. Gave it a try and when I run grub -> root <tab> it doesn't list any disks at all. I know I have a linux, windows and a another filesystem from looking at Disk Management on XP.

---

### Post by bodhi.zazen on 2007-07-03
LOL

It should not be *that difficult.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by OzzMosiz on 2007-07-10
I've got to a point now where Grub pops up at boot time, but selecting the Ubuntu to boot it doesn't work, XP does though. ubuntu can't find the device - any ideas?

---

### Post by OzzMosiz on 2007-07-22
*Bump* any ideas?

---

### Post by confused57 on 2007-07-22
Boot up the Ubuntu live cd and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Also, mount your root partition and post your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by sad_iq on 2007-07-22
Try this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

