---
title: "need help"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by uncertain143 on 2008-02-22
> root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/Windows
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda2 /media/Windows -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sda2 /media/Windows ntfs-3g defaults,force 0 0

it won't load windows, what seems to be the problem?

---

### Post by toa on 2008-02-22
> **uncertain143 said:**
> it won't load windows, what seems to be the problem?

Reboot into Recovery mode, reach the command line, and type

fsck 

it will go through a number of checks on the harddisk and check the drive and recommend remiving any allocated broken inodes, it hapens when you sudden shutdown or force reboot.

Then normal reboot.

---

### Post by spiderbatdad on 2008-02-22
Cleanly shutdown windows before booting Ubuntu.

---

### Post by zakirs on 2008-02-22
yes its seems to be because of forced shutdown .. go to windows and do a normal shutdown

---

