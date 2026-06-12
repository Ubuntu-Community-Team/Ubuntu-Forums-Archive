---
title: "extract .img"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-05-22
ellor guys im new and im tryin to edit and reconfigure some stuff for friends live cd distrib there are four .img files on it and i need to know how to either convert them or extract the files and one know the commands for this??:-?

---

### Post by tkjacobsen on 2006-05-23
if you want to extract it to a device eg /dev/sda1 use:
```
dd if=name.img of=/dev/sda1
```

Maybe you can just change the destination to a directory (eg of=/home/user/imagefolder)

Have not tried this myself, so be careful... Don't know if et works. Try to consult the manual: man dd

---

### Post by weldan on 2007-12-30
got it work. extract it to device like usb using dd

root# mount /dev/sdb1 /media/disk
root# dd if=/dir/filename.img of=/dev/sdb1
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.834497 seconds, 1.8 MB/s

and the extracted files are in /media/disk

---

### Post by darbid on 2008-06-24
just a small warning to beginners that stumble on this thread - the commands below which copy the img file to a USB device also wipe your device of anything else on it.

****edit - update

After doing more reading -  Be very careful with the dd-command also know to some people as Destroy Disk.  Your target in the above example WILL BE deleted and at this stage i have not found a recovery solution.

In my opinion dd-command is NOT for beginners because you get no warnings of what it is about to do.  I would suggest do not use it.

---

### Post by Balachmar on 2008-07-08
Although the extraction went fine, I cannot mount my usbdisk anymore. It doesn't recognise the FS....
How can I reformat the usbdisk? Or make it work?

---

