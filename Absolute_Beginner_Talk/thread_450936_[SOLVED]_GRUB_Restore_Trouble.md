---
title: "[SOLVED] GRUB Restore Trouble"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-05-21
Okay, I've got the usual problem where GRUB was overwritten by a Win reinstall. 

I've been trying the Super Grub Disk method.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I go through all the steps, get the appropriate screens and messages, and still GRUB is not restored. Only Windows boots.

Ubuntu is still there; I can boot the second drive with the Ultimate Boot CD.


Here's my annotated device.map,

(hd0)        /dev/hda     Windows
(hd1)        /dev/hdb     Ubuntu 6.10
(hd2)        /dev/hdd     just files


From menu.lst,

title                Ubuntu, kernel 2.6.17-11-generic
root                (hd1,0)
...
title                Windows 95/98/Me
root                (hd0,0)


How do I restore my GRUB?

---

### Post by kragen on 2007-05-21
You might want to try a guide specific to Ubuntu: See if this works:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

Good luck - if you have any problems following the instructions, or something goes wrong, post the details of what happened and I'll do my best to help.

---

### Post by louieb on 2007-05-21
so when you boot does the GRUB menu come up? or does it boot straight to window?
what about when use the UBD to boot the second drive does the GRUB menu come up? 
Your missing something simple or your computer is haunted. I like the Dual Boot site so much I've linked to it my signature. It has the solution to a lot of common GRUB problems.  

All your trying to do is change the MBR of hd0 to load the GRUB program stage2 which is in the /boot/grub/ directory of your Ubuntu install.

---

### Post by ofb on 2007-05-21
> **louieb said:**
> so when you boot does the GRUB menu come up? or does it boot straight to window?
what about when use the UBD to boot the second drive does the GRUB menu come up?

The GRUB menu does not come up at any point. Perhaps this is the missing detail: the Windows reinstall involved fdisking the first drive.

> All your trying to do is change the MBR of hd0 to load the GRUB program stage2 which is in the /boot/grub/ directory of your Ubuntu install.

Yes, that sounds right I think. That is what I would like to do.

I've no idea why the Super Grub Disk method does not work. I've tried several times. Everything proceeds as described, except on reboot it is Windows that boots - no GRUB.

---

### Post by ofb on 2007-05-22
Fixed.

Booted into Ubuntu with the Ultimate Boot CD, and used the first five-step part of this post:

How to restore Grub from a live Ubuntu cd
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

