---
title: "No check at start up"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-07-25
I followed instructions in another thread to stop the disk check of my XP drives - but I've obviously gone wrong somewhere, as now I get the black screen and "loading...", but then it goes straight to the Ubuntu logo and loading bar - no pre-GUI command echo at all. 

This is my current fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e27c3bdd-f406-4b36-bce0-43194b8f60d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=fc54f5d1-d567-4ef2-ab68-9bf356d1facd /home           ext3    defaults        0       2
# /dev/hda3
UUID=ACA6-45C0  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=CCE9-0485  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda6
# UUID=7e37592d-06d7-4dfd-bc27-2d507385d7df /media/hda6     ext3    defaults        0       2
# /dev/hda8
# UUID=d604cebf-6454-4408-8e62-36eb79fe84bb /media/hda8     ext3    defaults        0       2
# /dev/hda7
# UUID=1906c7b3-5404-4007-b673-cb047aa688db none            swap    sw              0       0
# /dev/hdb2
UUID=9bc9d7f8-c39b-4915-9802-fa3665f71fe5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Everything seems to be running OK, but I'm worried ....

TIA

---

### Post by dreadlord_chris on 2007-07-25
Not really sure what your problem is... are you wanting to see the boot text? If so you need to add something to your GRUB menu... Are you supposed to be dual-booting but only being allowed to boot Ubuntu? Again, this will be a change to your GRUB menu - not the fstab.

Need more information....

---

### Post by freesitebuilder on 2007-07-25
This was the original thread that I was looking at
[http://ubuntuforums.org/showthread.php?t=504342](http://ubuntuforums.org/showthread.php?t=504342)
Stopping fsck on non-Ubuntu partitions (my XP partitions have errors all the time!)

So (I thought) I had set no disk check on the XP partitions, but although everything runs OK, boot time is extremely fast, and I can't see any boot text, so I thought I'd made an error and the commands weren't being executed. I am dual-booting, and XP loads OK too.

I'm just paranoid :)

---

### Post by dreadlord_chris on 2007-07-25
> **freesitebuilder said:**
> This was the original thread that I was looking at
[http://ubuntuforums.org/showthread.php?t=504342](http://ubuntuforums.org/showthread.php?t=504342)
Stopping fsck on non-Ubuntu partitions (my XP partitions have errors all the time!)

So (I thought) I had set no disk check on the XP partitions, but although everything runs OK, boot time is extremely fast, and I can't see any boot text, so I thought I'd made an error and the commands weren't being executed. I am dual-booting, and XP loads OK too.

I'm just paranoid :)

if you'd like to see the boot text every time you boot up then you'll need to edit _/boot/grub/menu.lst_
open up a terminal:
```

sudo nano /boot/grub/menu.lst

```

Near the bottom - look for the line right after **## ## End Default Options ##**. It should be something like:
```

title           Ubuntu, kernel 2.6.20-16-generic

```
Your line might be a little different, doesn't matter. Look down 2 lines to the **kernel** line - do you see the word **quiet** there? Remove it. If it's not there it might be right below the **initrd** line - remove it as well if it's there.

Save the file - you should now see all your text when booting.

---

