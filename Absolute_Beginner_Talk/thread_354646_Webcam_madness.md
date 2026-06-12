---
title: "Webcam madness"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by h4m574h on 2007-02-06
Well, I'm trying to install drivers for some cheap-@ss webcam I have bought recently.  I tried to use easycam2 for drivers - but I guess it's just my luck that I get this error:
```
ERROR: Module sqcam does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.17-10-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.17-10-generic/kernel/drivers/usb/media/*': No such file or directory
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -f sqcam.o sq905.o sqcam.ko sqcam.mod.* .sq*.cmd 
#cp /usr/share/EasyCam2/drivers/sqcam/sqcam.ko /lib/modules/`uname -r`/drivers/usb/media/sqcam.ko
cp /media/usbdisk/Programmation/debian-cam/usr/share/EasyCam2/drivers/sqcam/sqcam.ko /lib/modules/`uname -r`/build/drivers/usb/media/sqcam.ko
cp: cannot stat `/media/usbdisk/Programmation/debian-cam/usr/share/EasyCam2/drivers/sqcam/sqcam.ko': No such file or directory
make: *** [install] Error 1

```
Googling failed to get me any results...help plz? ^w^

---

### Post by deadgobby on 2007-02-06
Here is how to install that Cheapo Cam.

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

Gobby

---

### Post by h4m574h on 2007-02-06
I used that guide to get Easycam2 in the first place.

---

