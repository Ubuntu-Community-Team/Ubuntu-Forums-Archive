---
title: "copy files using terminal"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by cleverlyinsane on 2007-08-13
I can not boot  my computer but can asscess a terminal mode and access my hard drive.  So i want copy my files that i have not back up yet ontoeither usb or cd. Iknow to use cp command but dont know the location of usb or cdrom. 

If i need to download i do have access to internet.

once, i get my flies out (20 or so) theni can reinstall or reformat

Thanks, hope someone can help
Dan

---

### Post by Arisna on 2007-08-13
It would probably be easiest to put the files on a USB drive.  Command line CD burning is a bit of a chore.  If you don't have any graphical environment running, the USB device will probably not be mounted automatically.  You'll need to check the output of the command "dmesg" to see what device node it has been assigned, probably something like /dev/sda1.  You'll then need to do a "sudo mkdir /media/usbdisk" or similar and "sudo mount /dev/sda1 /media/usbdisk".  That will let you access the USB device at /media/usbdisk.

---

### Post by cleverlyinsane on 2007-08-14
thanks for your help, trying to go usb way.

I have done the 1st part, creating new dircetory ok, but when dothe secondd part, 

 the USB device will probably not be mounted automatically.  You'll need to check the output of the command "dmesg" to see what device node it has been assigned, probably something like /dev/sda1.


and "sudo mount /dev/sda1 /media/usbdisk".  That will let you access the USB device at /media/usbdisk.

this is the error i get,
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/sdb1/media/usbdsk in /etc/fstab or /etc/mtab

so much fun:p

I tried to edit sudo gedit /etc/fstab but it says cannot open display

---

### Post by RomeReactor on 2007-08-14
Hi. Try using nano to edit fstab from the command line:
```
sudo nano /etc/fstab
```
Press CTRL+O to save any changes, and/or CTRL+X to close it.

---

### Post by cleverlyinsane on 2007-08-14
Thanks, now what does the line that i need to add  looks like

---

### Post by Rul on 2007-08-14
I think it should look like this

```


/dev/sdb1 /media/usbdisk vfat defaults 0 0


```

/dev/sdb1 is the place where the usb hub is in my computer, /media/usbdisk is the mounting point, looking at my usb stick it says it's format is vfat.

---

### Post by cleverlyinsane on 2007-08-14
one step closer, 

/dev/sdb1 is the place where the usb hub is in my computer, /media/usbdisk is the mounting point, looking at my usb stick it says it's format is vfat.[/QUOTE]

how do you find the format of the usb, i tried vfat and ext3, niether works?

slowly getting there the message i get is, 
mount point vfat does not exist.

same with ext3

---

### Post by Rul on 2007-08-14
I was able to mount my usb using the command line using this
```

sudo mount -t vfat /dev/sdb1 /media


```

it mounted in media, even when I hadn't change the fstab file, and the default directory for my usb is /media/disk, so it should work for you. If vfat and ext3 doesn't work, you can try ntfs.

to unmount the usb I just typed

> 
sudo umount /media



---

