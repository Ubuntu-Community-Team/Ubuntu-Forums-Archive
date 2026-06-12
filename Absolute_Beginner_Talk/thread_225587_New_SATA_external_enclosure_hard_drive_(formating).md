---
title: "New SATA external enclosure hard drive (formating?)"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by sleepjump on 2006-07-29
Hi guys, I went out today and bought a 200gb sata hard drive then bought an external enclosure for it, making it an external drive via usb. My question is, how do i format this drive, and will it be possible for the drive to be read on this ubuntu computer, and also on another windows computer?

---

### Post by sleepjump on 2006-07-29
oops i forgot to search before posting, found this great guide. sorry about that!

[http://www.ubuntuforums.org/showthread.php?t=224250&highlight=external+hard+drive+format](http://www.ubuntuforums.org/showthread.php?t=224250&highlight=external+hard+drive+format)

---

### Post by catlett on 2006-07-29
It should be auto detected and an icon appear on the desktop when you connect it and power on the drive.
If that hapens then you can format it with gparted. Go to System<Administrations<Gnome partition editor. That is gparted. If it isn't there run this command to install it and then go back to the menu
```
sudo apt-get install gparted
```
The easiest file system to use is fat32. Both windows and linux can read/write to it. The only drtaw back is the 4gb file size limit.
You could format it ext3 the linux filesystem type but you have to install a driver for windows to read/write to it. The link to it is in my signature.
Gparted can format the drive to either type.

---

