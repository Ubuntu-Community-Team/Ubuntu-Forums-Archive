---
title: "Hard drive adding and removing questions"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by lawson23 on 2007-04-06
Ok here is the situation.
I first installed with a 20GB master (with windows on it) and a 40GB slave I put edgy server on.

Grub went on the 20GB drive to control booting.  I want to remove this drive from the box.

First Question:
How do I pull this drive and get the 40GB (moved to master) bootable for edgy.

Then I want to add a new Hard Drive 250GB.  

Second Question:
How do I get edgy to see this drive as a XFS to /var/lib/?

Currently I have a portion of the 40GB as XFS to /var/lib/  I would like to eliminate this space after I do the new drive addition and add it to my primary ext3 which is like 4GB on the 40GB drive.

Is this all possible without losing data?

Thank you for all the help.

---

### Post by steve.horsley on 2007-04-06
Grab a copy of the "alternate" installer CD. It has a handy rescue mode.
Boot Ubuntu and edit /etc/fstab to use hda instead of hdb next time it boots.
Swap the 40G to make it master. At this point the PC can't boot.
Boot the installer CD and chose to "Rescue a broken system". Once you have a command prompt on the broken Ubuntu, use this command:
**grub-install /dev/hda**

Once you have a working Ubuntu on hda, you can add the 250G drive and use gparted to format it. Once formatted, you will want to mount it somewhere like /media/hdb1 and then (as root) copy /var/lib to it. Then unmount it and mount it at /var/lib instead. Add this to /etc/fstab to make it happen every time you boot.

---

### Post by lawson23 on 2007-04-07
I already have the alternate disc so I will try as you mention below.  Thanks for the help by the way.

---

### Post by lawson23 on 2007-04-07
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e1afaa75-be81-437a-9432-5988ef908323 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=E87C44B37C447DF6 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=524de263-64b0-4be3-815d-b43f6d70aa92 /var/lib        xfs     defaults        0       2
# /dev/hdb2
UUID=fd3641d5-793e-4409-94e4-2fbdd3fe9ce1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```
May I ask what here I edit as it doesn't give any details to what defines the boot setting.

---

### Post by lawson23 on 2007-04-08
I just found this guide that I'm going to check out if anyone has different recommendation let me know.

[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by lawson23 on 2007-04-08
Ok the first article didn't give me much info but it did point to this which is pretty descriptive but I still don't see anything I'm looking for.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by steve.horsley on 2007-04-08
Aha! Since it's using UUIDs insead of /dev/xxx to identify the drives (the UUID is the identity embedded in a partition as it's formatted), you shouldn't have to edit anything - it should just find the partition on its new location and mount is as before.

---

### Post by lawson23 on 2007-04-08
So I don't have to edit this file and start here:

> Swap the 40G to make it master. At this point the PC can't boot.
Boot the installer CD and chose to "Rescue a broken system". Once you have a command prompt on the broken Ubuntu, use this command:
grub-install /dev/hda

Once you have a working Ubuntu on hda, you can add the 250G drive and use gparted to format it. Once formatted, you will want to mount it somewhere like /media/hdb1 and then (as root) copy /var/lib to it. Then unmount it and mount it at /var/lib instead. Add this to /etc/fstab to make it happen every time you boot.

---

### Post by lawson23 on 2007-04-08
```
grub-install /dev/hda
```
Except I take it I don't use /dev/hda
What would I use?

---

### Post by lawson23 on 2007-04-08
after running:
```
grub-install /dev/hda
```
I get:
> The file /boot/grub/stage1 not read correctly

---

### Post by steve.horsley on 2007-04-09
That's a blow, and I don't know what could be causing that. The rescue CD will allow you to verify that /boot'grub exists. Actually, I wonder if something is still thinking that it should be reading /dev/hdb/boot/grub. Perhaps /boot/grub/device.map? You could try the command 
grub-install (hd0)
but may get the same error. If so, all I can think of is to check that device.map points to the right device and to then retry the install. After that, all I can think of is to try and install grub using the grub installer from [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/) or to give in and use the Ubuntu installer.

---

### Post by lawson23 on 2007-04-10
```
grub-install (hd0)
```
produces the same result
On to looking into the other things mentioned.

---

### Post by lawson23 on 2007-04-14
I have been trying to get to the Super Grub Disk but without luck.

Is this now not available?  I seen he updated it on 3-27 but I can't get to the site.
[http://forjamari.linex.org/frs/download.php/533/sgd_0.9588.iso.gz](http://forjamari.linex.org/frs/download.php/533/sgd_0.9588.iso.gz)

Anyone else know where I can get this tool?

---

### Post by lawson23 on 2007-04-16
I can now reach the site and boot my drive.  I can boot the linux setup with this disk.  Now I have to figure out how to get grub installed and working on the drive.

----------------------------------------------------------
I did use the super grub disk to try and rebuild grub (it has this option) and it now displays a menu when booting but when selecting Linux it doesn't do anything.

---

