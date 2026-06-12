---
title: "[SOLVED] Kubuntu 6.10 Help"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by sudeep on 2008-01-16
Hi To All Frnds,

Yesterday i installed Kubuntu 6.10 on my DELL Desktop.Everything went very Fine.I am haapy. But one problem i got.When i inserted My USB Pendrive. It was unable to mount.In the /media the device for USB was not listed.only cdrom0 and floppy were there....

Following things happened...After i inserted Pendrive.

New Removable Media Detected.

But Media Type was unmounted.
Some actions were listed to be done.but nothing was happening at last.

So how to mount so that i can access pendrive data.

Plz Help
Regards,
Sudeep

---

### Post by ajmorris on 2008-01-16
hi there,
to mount that USB device, do:
```
sudo mkdir /media/disk
```
then
```
sudo fdisk -l
```
this will output your hard disks, and removable devices, the usb drive will be something along the lines of /dev/sdb1
so then do:
```
sudo mount /dev/sdb1
``` (where sdb1 is your device)
also, note: you may need to specify a type that the USB drive is (sudo fdisk -l should also tell you the type) to specify the type, do sudo mount -t <type> /dev/sdb1 (also -t auto can be specified to let linux try to detect the file system type)

Then, to make it automatically boot, you can add an entry for it to /etc/fstab.

However, you do not need to delve into all this, i suggest.. if its possible for you to do so... to do a full system upgrade to the latest kubuntu (gutsy), because gutsy has a utility in it called hotplug, this automatically mounts external devices such as your USB flash disk, without you having to delve into all of this.

Best of luck!!

---

### Post by sudeep on 2008-01-16
Thanx Frnd,

I will try today....

Regards,
Sudeep

---

