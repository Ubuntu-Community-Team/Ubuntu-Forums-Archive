---
title: "USB stick not responding"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by TpyKv on 2008-04-17
Hello!

I have been using a USB stick for about a month, going between various windows machines and to my new Ubuntu laptop...

All has been well, until recently, Ubuntu recognises the drive, opens the folder, but then hangs and will not respond. 

It works fine in XP & Vista,,,

I have transferred all the info to XP, reformatted it, and put the info back on again. Still it will not load.

I went to the terminal., typed mount -l and it says:

 /dev/sda1 on /type ext3 (rw,errors=remount-ro) 

this is wierd - I know linux uses the ext3 filesystem but I formatted it to FAT32 under windwws before trying it in Ubuntu again...

does anyone have any suggestions? maybe I should remount it?? not sure now to do that??

THANKS ALL!!

---

### Post by wolfen69 on 2008-04-17
first go to system>preferences>removable drives and media and check to see if the first box is checked. if it is, see below. if it's not, check it off and see if that works.

try this, without usb stick in machine.
```
sudo mkdir /media/usbstick
```
```
gksudo gedit /etc/fstab
```
create new line:
/dev/sda1      /media/usbstick   vfat  user.rw,noauto,exec 0   0

with cursor at the end of that line, hit enter. (as if you were starting a new line)

then save file.

if the stick will not open automatically, you will have to mount it manually with:
```
sudo mount /dev/sda1
```
then you can navigate to it through your file browser.

---

### Post by TpyKv on 2008-04-17
Thanks for the quick reply! 

This didn't work, well it mounted but it still won't allow me to access the files, it just freezes up and asks me if I want to force-quit....

it's not liking me today :)

---

