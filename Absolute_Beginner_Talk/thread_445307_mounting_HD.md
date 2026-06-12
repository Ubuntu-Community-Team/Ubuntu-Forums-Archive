---
title: "mounting HD"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Luis1982 on 2007-05-15
I want to mount a hard drive on Linux. I'm running linux and this other HD has Windows XP. I want to have the option of double booting. How can I do this?
Thank you for your help

---

### Post by nightskywind83 on 2007-05-15
To mount your XP harddrive manually, follow the instructions on this page:

[https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29](https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29)

To mount your XP harddrive automatically whenever you boot, follow the instructions on this page:

[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

When you installed Ubuntu, it should have installed GRUB to your Windows MBR, and when you boot you should have a choice of Ubuntu or Windows.  Is this not happening?

Let us know any further questions/concerns.

Regards,
Andy

---

### Post by Luis1982 on 2007-05-15
nightskywind83, my problem is that when I installed Linux, first I disconnected the hard drive that have Windows XP and after Linux completed the install I connected the hard drive with Windows. Maybe that was my mistake. I want to be able to see my two hard drives in the OS and also I want to have the option to choose the OS I want to run my computer. I appreciate your help

---

### Post by krisfrajer on 2007-05-15
oiga... conectase en el msn
o llameme

---

### Post by alienexplorers on 2007-05-15
First of all you should have left the Windows hard drive in.  That way when you loaded Ubuntu it would have set up dual boot for you.  You now have to setup grub to detect your OS'es.  If grub recognizes Ubuntu you might be able to add the section below to get windows into grub.

Enter terminal and type:

> gksudo gedit /boot/grub/menu.lst

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Save the menu.lst fire and reboot.

---

