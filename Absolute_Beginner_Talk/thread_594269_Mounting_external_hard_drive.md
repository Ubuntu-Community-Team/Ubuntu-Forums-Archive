---
title: "Mounting external hard drive"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-27
I backed up all my stuff on my friend's external hard drive.  I expected it to automount like my USB key, but it doesn't.  How do I mount it?  It is a Seagate drive that connects through USB, but it has it's own power source.  Any help?

---

### Post by taurus on 2007-10-27
See if you can mount it by hand from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
df -h
```
I assume your USB drive is /dev/sdb1 and it is ntfs filesystem.  If not sure, post the output of this command from a terminal first before you run those three commands above.

```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by TheOrangePeanut on 2007-10-27
This is the output of sudo fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4982     1686825    5  Extended
/dev/hda5            4773        4982     1686793+  82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x563dbccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    c  W95 FAT32 (LBA)

---

### Post by logos34 on 2007-10-27
system>prefs>removable drives & media>storage tab> check mount removable drves when hot-plugged

does that help?

---

### Post by TheOrangePeanut on 2007-10-27
It's already checked.

---

### Post by taurus on 2007-10-27
It's /dev/sda1.

```
sudo mkdir /media/sda1 <- You could get a message that it is already exit.
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
ls -la /media/sda1
```

---

### Post by TheOrangePeanut on 2007-10-27
Okay, I can ls -la /media/sda1 and see the files in the terminal, but how can I see them graphically?  I have to copy about 15 gigs of stuff from the external HDD to my internal, and I don't know how to do that from the command line.  It isn't showing up in Nautilus, either.

---

### Post by taurus on 2007-10-27
You have to browse to /media/sda1 to see them.  Keep hitting the up arrow in nautilus until you get to /.  Then, you would see a directory called media.  Click on that to change to that directory in nautilus and you should now see a sda1.

---

