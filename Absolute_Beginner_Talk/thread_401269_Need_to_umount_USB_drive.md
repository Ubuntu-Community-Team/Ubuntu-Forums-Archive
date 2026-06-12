---
title: "Need to umount USB drive"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Netspeed on 2007-04-04
I need to umount my USB drive in order to get it to work with VirtualBox.

I terminaled "sudo gedit /etc/fstab" it opened up a new window with this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=554ed2be-abb0-4bfe-a873-49334837fab2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ca802f39-ba83-467d-9e1e-20d28e57021c none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I don't see the USB drive.

---

### Post by Kobalt on 2007-04-04
Which version of Ubuntu are you running ? Which format is your USB drive ? 
If you want some more help on mounting drives/partitions, check [this]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mount&titlesearch=Titres") out.

---

### Post by Netspeed on 2007-04-04
I'm running Edgy....how do I see the format of the USB drive?

---

### Post by Kobalt on 2007-04-04
When you have it plugged, what is the output of the following command line 
```
sudo fdisk -l
```

---

### Post by Netspeed on 2007-04-04
Thanks for all the help!
Output is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29656   238211788+  83  Linux
/dev/sda2           29657       30401     5984212+   5  Extended
/dev/sda5           29657       30401     5984181   82  Linux swap / Solaris

---

### Post by mcduck on 2007-04-04
Removable drives are not handled through fstab. To unmount just right-click the icon on your desktop and select 'Unmount' or 'Eject'. From terminal, use 'sudo umount /dev/yourdevice'. To get the right device use the 'mount'-command to list all mounted devices.

---

### Post by Kobalt on 2007-04-04
Is it an USB drive you just bought or did you use before (in Win/Mac OS) ?

---

### Post by etank on 2007-04-04
I have a usb drive that is formatted as NTFS. I intstalled ntfs-3g and then added this to my fstab file ```
/dev/sdb1     /media/usbdrive     ntfs-3g     users,silent,umask=0002,locale=en_US.utf8,no_def_opts,allow_other    0    0
```
I had to add myself to the fuse group and also create the /media/usbdrive dir for it to work. Your device may or may not be /dev/dsb1 though.

---

### Post by Netspeed on 2007-04-04
It doesn't show up on my desktop and the "mount" command came back with this as the only remotely listed as a USB:

procbususb on /proc/bus/usb type usbfs (rw)

---

### Post by Netspeed on 2007-04-04
It's a pair of Logitech USB headphones and they've worked before. The big problem is that I'm having trouble getting them to work in XP running in VirtualBox.

---

### Post by Kobalt on 2007-04-04
> **Netspeed said:**
> It's a pair of Logitech USB headphones and they've worked before.
Wait wait wait, you wrote before that it was an USB drive, you didn't mention headphone ?
Is it a storage device or headphones ?

---

### Post by Netspeed on 2007-04-04
Sorry...yes they are headphones. I thought that all USB devices would be seen the same way.:oops:

---

