---
title: "Xubuntu (un)mounting query"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by 3rdalbum on 2006-02-24
Hi. I've just switched to Xubuntu and since I'm not a hardcore Linux hacker, I'm having trouble with mounting my Zip disks.

I downloaded mountpy from Synaptec because I can't figure out all the mount points and /dev folder and stuff, and the first time I ran the program it mounted my Zip disk (/media/sda1). I then unmounted it using umount. I tried mounting it again using mountpy, and this time it told me that it couldn't find anything to mount.

Double-clicking on the /media/sda1 folder doesn't remount or access the disk. In fact, the drive isn't even showing up in HAL Device Manager anymore. I've tried unplugging it and replugging it in, but to no avail.

Automatically mounting and unmounting worked perfectly in normal Ubuntu... what's going on here? Also, is there any program that will automatically mount and unmount in Xfce?

---

### Post by mtron on 2006-02-24
i'm currently @ work, but from my memory: the automount in gnome is done via the gnome-volume-manager so install it with nautilus and gconf-editor. 

after the install run gconf-editor from a terminal and disable the "take over desktop" setting (i don't remember the exact name though), if you do this, nautilus will manage the mounting of these usb or firewire devices that are supportet.

Concerning the other question. 
read some basic info about mounting: [https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29)

If your drive is really not working, check dmesg (in terminal) for a starting point where the error might be, also if the drive is usb, you can try "lsusb" to get some debug info

---

### Post by 3rdalbum on 2006-02-25
Thanks for the advice, I think I might put those programs back on. Especially nautilus - I hate rox.

Today when I booted up I had no trouble with the drive, so it must've been a gremlin.

---

### Post by firehead_eom on 2006-05-15
[QUOTE=mtron]
after the install run gconf-editor from a terminal and disable the "take over desktop" setting (i don't remember the exact name though), if you do this, nautilus will manage the mounting of these usb or firewire devices that are supportet.[/QUOTE]

the "take over desktop setting is located in the following **gconf-editor** menu : 

**/** > **apps** > **nautilus** > **preferences** > **show_desktop** (untick this)

Hope this helps.
:)

---

