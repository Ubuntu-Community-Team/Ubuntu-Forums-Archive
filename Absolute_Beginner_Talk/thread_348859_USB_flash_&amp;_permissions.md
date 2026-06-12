---
title: "USB flash &amp; permissions"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-01-29
Small problem but how do I change permissions for a USB flash drive?  I don't recall setting any on this drive but I tried to use it to transfer photos from my home/photos folder to my wife's home/photo folder but it said she didn't have permissions to access the flash drive.  I can view the permissions via Properties of drive but can't set/change in that window.
Thanks.

---

### Post by t4thfavor on 2007-01-29
chmod is used to change file permissions, but you may be able to use "sudo cp /usbdrive/pictures /wifesdirectory/pictures" to get the copy to go through.

Thanks

---

### Post by punkybouy on 2007-03-13
This worked for me when I had the same problem.
if its ext3 do the following:
1. Open a terminal
2. Type "sudo chown [your username] /media/nameoftheusbdrive". Press enter
3. Type "sudo chgrp [your username] /media/nameoftheusbdrive". Press enter again.

---

### Post by bmenge on 2007-03-13
I encountered the same problem today.  I tried what was stated above still could not copy and paste in the gui.  I know it would be possible to do it in the terminal but I don't want to have my wife deal with that she wouldn't go for it.  She has been dragging and dropping stuff on a normal basis with the usb disk and now it has this problem too.

---

### Post by bmenge on 2007-03-19
bump

---

### Post by bmenge on 2007-03-27
I tried a few different things and still not working

brian@brian-desktop:/media/usbdisk$ sudo chown brian /media/usbdisk
chown: changing ownership of `/media/usbdisk': Read-only file system

brian@brian-desktop:/media/usbdisk$ sudo chgrp brian /media/usbdisk
chgrp: changing group of `/media/usbdisk': Read-only file system

brian@brian-desktop:/media/usbdisk$ sudo chmod ug+rw /media/usbdisk
chmod: changing permissions of `/media/usbdisk': Read-only file system 

why am I still getting the read only file system?

---

### Post by bmenge on 2007-03-27
ok I am an idiot I didn't know they drive had a lock slider on it. all is well now

---

