---
title: "usb key doesnt work"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by obb2007 on 2007-06-06
i have a 2gb, usb kingston drive and it stopped working in ubuntu. i ahve ntfs read/write enabled. i formatted the drive in linux for fat 16 and tried fat32 as well. ormatteed in windows but it just doesnt mount. when i plug it in its icon is shown briefly then dissapear.
any solution?
thanks

---

### Post by Inxsible on 2007-06-07
can you post the output of ```
 sudo fdisk -l
```

make sure you drive is connected while you do this

---

### Post by obb2007 on 2007-06-07
thats the output. i also tried to mount it with gnome partition manager. it looks like it mounts it, but it doesnt shows on the desktop nor in the computer folder.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         251     2015200+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 39)

---

### Post by obb2007 on 2007-06-08
anyone? without usb drive working there's no point for me to use ubuntu...
thanks

---

### Post by Campingman on 2007-06-08
Hi, try this, I have to mount my usb devices manually on some occasions, it may work for you:
In a terminal type dmesg, the output should give you a clue as to what the device is labelled usually sda1,sdd1, sda2 etc

Then try to mount the device manually:
Create a folder in your file system/media folder as a mount pount, say you created a folder named usb
In a terminal enter:

sudo mount -t vfat -o rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 /dev/name of your drive /media/usb

This assumes the drive is still fat.
Hope this works for you

---

### Post by obb2007 on 2007-06-09
thanks, but it's still only mounted in that folder and i can only read (although i enabled ntfs full write suppot for internal and external devices) plus, it contains some files with hebrew names that appere as as lines of question marks instead of letter)

---

### Post by handydan918 on 2007-06-09
> **obb2007 said:**
> thanks, but it's still only mounted in that folder and i can only read (although i enabled ntfs full write suppot for internal and external devices) plus, it contains some files with hebrew names that appere as as lines of question marks instead of letter)

If the key is mounted, it is mounted. It really doesn't matter where it is mounted. The hebrew names thing is probably a fonts issue.

---

### Post by obb2007 on 2007-06-09
it's mounted but no write support. and i have all the possible fonts, it's the system can't read it from some reason. i have no problems with websites at all.

---

### Post by drowner on 2007-06-09
I get the feeling it may be corrupted

Odd characters, randomly becoming read-only, the odd fdisk output... have you been doing funny things with it? Like letting windows hibernate with it plugged in, then booting ubuntu? Or leaving plugged in with windows and not shutting down properly?

---

### Post by Jimmyfj on 2007-06-09
You should try this out:

First - Open a terminal-window

Code:

Sudo apt-get install autofs

automount /dev/your key's name /media/usb

After installation be sure that your thomb-drive/stick is placed in a USB-port that works.

Jimmy

---

### Post by domer on 2007-06-12
When I plug in my USB key on my laptop (Compaq V2000), there is [COLOR="Red"]**no desktop icon**[/COLOR], even though I could read/write from/to the drive. The same USB key when plugged on my desktop shows a desktop icon (which makes it easier to eject the USB key). Does anyone have a fix for this annoying issue? 
Thanks a lot.

---

