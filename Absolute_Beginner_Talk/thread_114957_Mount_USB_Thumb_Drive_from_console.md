---
title: "Mount USB Thumb Drive from console"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by kleptos on 2006-01-09
I will be installing Ubuntu Server 5.10 tonight on a computer i want to use for development. I know server doesnt immediatly have the gnome system on it. Is there a way to mount a usb drive from the command line and access files on the drive?

---

### Post by lindejos on 2006-01-09
I don't know if this applies but when I installed Breezy on my pc all the usb ports were automatically set up.  As soon as I stuck the thumb drive in it mounted to the desktop.

---

### Post by Greg2 on 2006-01-09
[QUOTE=kleptos]I will be installing Ubuntu Server 5.10 tonight on a computer i want to use for development. I know server doesnt immediatly have the gnome system on it. Is there a way to mount a usb drive from the command line and access files on the drive?[/QUOTE]
If the usb modules are loaded you should be able to do it.

Insert the usb drive and use dmesg to see if it was recognized. If so, it should show up as sda or sda1 if you are not using anything else on the usb hub? So depending on if it shows up, and what it shows up as do:```

sudo mkdir /mnt/removable
mount /dev/sda /mnt/removable
cd /mnt/removable
ls
```

You may have to use an option like:```
mount –t vfat /dev/sda1 /mnt/removable
``` or whatever the filesystem is on your usb drive if you get an error about filesystems?

---

