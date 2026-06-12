---
title: "automounting usb disks"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-25
i was wandering if it's possible to mount a specific disk in a predetermined folder.

My NTFS usb disks always mount in /media/sdX but they show on my desktop with the name like Odin or whatever     
I named them but my EXT3 usb disks mount with a generic usbdisk name produced by the system.

I have to unmount then remount in a folder which name i want to show on the desktop.

is it possible to make ubuntu recognize my disks and mount them in a specific folder so i can get the name on my dekstop?
perhapse a little script on the disk to identify it?

---

### Post by Engnome on 2006-10-25
> **zekopeko said:**
> i was wandering if it's possible to mount a specific disk in a predetermined folder.

My NTFS usb disks always mount in /media/sdX but they show on my desktop with the name like Odin or whatever     
I named them but my EXT3 usb disks mount with a generic usbdisk name produced by the system.

I have to unmount then remount in a folder which name i want to show on the desktop.

is it possible to make ubuntu recognize my disks and mount them in a specific folder so i can get the name on my dekstop?
perhapse a little script on the disk to identify it?

/etc/fstab keeps track of which partitions to mount where. But I'm not sure changing mount point will change name of the folder on your desktop. Try it and report back! Just be careful editing that file, don't touch / and /home unless you know what youre doing.

---

### Post by MyAnda on 2006-10-25
you might look into udev rules...

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by bodhi.zazen on 2006-10-25
> **zekopeko said:**
> i was wandering if it's possible to mount a specific disk in a predetermined folder.

My NTFS usb disks always mount in /media/sdX but they show on my desktop with the name like Odin or whatever     
I named them but my EXT3 usb disks mount with a generic usbdisk name produced by the system.

I have to unmount then remount in a folder which name i want to show on the desktop.

is it possible to make ubuntu recognize my disks and mount them in a specific folder so i can get the name on my dekstop?
perhapse a little script on the disk to identify it?

Make an entry in fstab by LABEL.

To find the label of your usb device:```
ls /dev/disk/by-label
```

Then:```
LABEL=<label> /media/<desired_name> auto users,noauto,rw 0 0
```

[How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

