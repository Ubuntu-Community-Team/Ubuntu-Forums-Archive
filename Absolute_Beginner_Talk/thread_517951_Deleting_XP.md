---
title: "Deleting XP"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-05
What is the safest or quickest way to wipe XP from my hard drive without "breaking" ubuntu?

---

### Post by logos34 on 2007-08-05
Use Gparted
[B]
sudo gparted[/B]

format the winxp pro partition as ext3.  One thing you could do with it is [make a /home partition.]("http://www.psychocats.net/ubuntu/separatehome")

Remove windows entry from your grub menu screen:

**gksudo gedit /boot/grub/menu.lst**

delete xp entry at bottom

Edit fstab:

**gksudo gedit /etc/fstab**

remove line for windows

---

### Post by nphx on 2007-08-05
If Grub is loaded on the master boot record, you can just use Gparted (sudo aptitude install gparted) to wipe out the Windows XP partition. Then just remove or hide (with # comments) the kernel entries from grub menu, located in [COLOR="Red"]/boot/grub/menu.lst[/COLOR]:
[B]
Make this section:[/B]

> title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

**look like this:**

> ##title           Microsoft Windows XP Professional
##root            (hd0,0)
##savedefault
##makeactive
##chainloader     +1

---

### Post by fraser_m on 2007-08-05
In GParted the XP partition is locked (has a padlock symbol.) I have tried unmounting it but it says:
```
umount: /dev/sda1 mount disagrees with the fstab
```

How can delete it?

---

### Post by logos34 on 2007-08-05
Then delete the windows entry fstab first to prevent it from mounting at boot.  Reboot.  Now you should be able to use gparted to delete it.

---

### Post by fraser_m on 2007-08-05
that's sudo gedit /etc/fstab right?

---

### Post by logos34 on 2007-08-05
> **fraser_m said:**
> that's sudo gedit /etc/fstab right?

no actually you want to use 'gksudo' when opening applications from the terminal (it's a safety measure).

---

### Post by fraser_m on 2007-08-05
If I delete the XP partition and move swap so it's at the start of the drive, then expand root so it fills the rest of the drive will GRUB still load?

If you need more info I can tell you.

---

### Post by fraser_m on 2007-08-05
Here is a OK txt diagram of my gparted drive

---

### Post by logos34 on 2007-08-05
you mean your setup was
windows-->ubuntu root-->swap

and you want to change change it like this

swap-->ubuntu

?

In that case the uuid for swap will change.  Grub may or may not boot ubuntu, even though in theory ubuntu root would still be at (hd0,1)  i.e. sda2, the second partition

---

### Post by fraser_m on 2007-08-05
The best bit about your reply is the "in theory" bit.

But I'll try it anyway!!! ;)

---

### Post by logos34 on 2007-08-05
if I understand that txt diagram correctly, then ubuntu was sda3? (i.e. hd0,2)  with swap in between?

If so, then you'll ned to change /boot/grub/menu.lst to read (hd0,1) and edit root entry in fstab.  (and take out those uuids)

---

