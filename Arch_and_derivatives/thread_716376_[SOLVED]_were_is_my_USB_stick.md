---
title: "[SOLVED] were is my USB stick?"
date: 2008-03-05
forum: Arch and derivatives
---

### Post by chris200x9 on 2008-03-05
I know in ubuntu it in /media/disk but in arch I can't find it!

---

### Post by PurposeOfReason on 2008-03-05
Have you installed HAL?

pacman -S hal

---

### Post by chris200x9 on 2008-03-05
no......I'm in a catch 22 I have the mad wifi drivers to get online with my wireless card on my usb stick and now it turns out I need to install HAL to get to my usb stick....

---

### Post by fwojciec on 2008-03-05
You can always mount it manually...

Make a mountpoint somewhere in /mnt, something like "mkdir /mnt/usb" for example, and then just mount it using the mount command.  You might need to look up the /dev name of the usb stick using "fdisk -l" command, once you know what it is just do "mount /dev/sd?? /mnt/usb".

All the commands must be issued as root, by the way.

You also might need to specify the usb stick filesystem type -- if it's fat the command would look like this, for example: "mount -t vfat /dev/sd?? /mnt/usb"

---

### Post by chris200x9 on 2008-03-05
thank you so much!

---

