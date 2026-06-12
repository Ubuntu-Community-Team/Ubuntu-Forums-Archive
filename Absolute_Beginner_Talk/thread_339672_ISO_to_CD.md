---
title: "ISO to CD ???"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-01-16
Hi there,

I have a Win XP x64 ISO file on my computer. I want to install Windows using vmware server, since I'll be using Photoshop, Flash, etc... on it.

Which is the best way to do this?
Can I boot from the iso file?
If not.... (which I doubt), which is the best way to write the ISO to make a bootable disk? What software will I use?

Thank you very much in advance. ;)

---

### Post by deadgobby on 2007-01-16
The XP ISO most like to be a bootable CD. To burn it using Linux. I would use K3B. Burn the ISO at least 10x speed. Once the ISO is completed on the CD. Reboot the system. Make sure your BIOS is set to boot from CDROM first. Windows does not other like O/S on the same drive. So if you want you Linux partition. It is going to go away. So I would back up every thing as you can and go for dual boot. So install XP first and Linux 2cd.

Gobby

---

### Post by rai4shu2 on 2007-01-16
There are several threads here on vmware you can use, like this one:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by Canis familiaris on 2007-01-16
In the VMWare console, edit the setting, select the cdrom and instead ask it to use the XP ISO image instead of Physical drive, make sure that Power On this Device is Checked.
Now your VM will boot using the ISO image.
Make sure after installing, reselect the physical drive from he same menu.

---

### Post by Contrid on 2007-01-16
Guys, thank you very much!!!
I got everything sorted out as it should be, and I'm now installing WinXPx64.
Sorry if it was a stupid question...I just haven't ever done this in Ubuntu.
Thanks again for the help. ;)

---

