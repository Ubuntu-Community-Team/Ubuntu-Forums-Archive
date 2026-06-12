---
title: "[SOLVED] quick noob question - archives on desktop"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-07-11
I've got several disk icons on the desktop by default. Two of them are dell restore partitions. Are these icons similar to shortcuts and thereby safe to delete? Or will deleting them actually affect the partitions in some way?

---

### Post by kevinlyfellow on 2007-07-11
I don't think you can delete, but if you can you don't need to worry about it deleting your partition

Try instead to unmount them

---

### Post by moredhel on 2007-07-11
If you install gtweakui then you can make it remove them, but bare in mind it will do all your others as well.

---

### Post by OliverN on 2007-07-11
> **kevinlyfellow said:**
> I don't think you can delete, but if you can you don't need to worry about it deleting your partition

Try instead to unmount them

well, can't unmount, and I see I can't delete either.

> **moredhel said:**
> If you install gtweakui then you can make it remove them, but bare in mind it will do all your others as well.

thanks, but is there no other way that allows me to keep the ones I want?

---

### Post by moredhel on 2007-07-11
I'm not sure, but there sure should be!

---

### Post by OliverN on 2007-07-11
> **moredhel said:**
> I'm not sure, but there sure should be!

lol, yeah

---

### Post by Medieval_Creations on 2007-07-11
This is one of the drawbacks I personally dislike about Genome.  I'm not sure if it's just an Ubuntu thing.  But any Folder that is mounted in /media will show up on your desktop.  I personally avoid this by mounting any other drives or partitions I want under /mnt.

My suggestion would be to edit /etc/fstab.
Comment out the lines for the partitions you don't need to see/use and reboot.  This will not delete any of the partitions, it just does not mount them by default.

---

### Post by Tommerz on 2007-07-11
Medieval's idea sounds good, just hit alt+f2 and then type gksu gedit /etc/fstab and then press enter then put a # in front of any partitions you don't want to use in ubuntu.

It's a complicated way round it, it may be worth you installing gtweakui through synaptic and doing it that way instead then just creating shortcuts to your drives afterwards :).

---

### Post by kevinlyfellow on 2007-07-11
> **moredhel said:**
> If you install gtweakui then you can make it remove them, but bare in mind it will do all your others as well.

Actually, you don't need to install anything, the option is in gconf
```
gconf-editor /apps/nautilus/desktop/volumes_visible
```

---

### Post by OliverN on 2007-07-11
> **kevinlyfellow said:**
> Actually, you don't need to install anything, the option is in gconf
```
gconf-editor /apps/nautilus/desktop/volumes_visible
```

But I like the feature that newly mounted drives (like usb drives or dvds) show right away on the desktop, so I think I'm gonna go with:

> **Tommerz said:**
> Medieval's idea sounds good, just hit alt+f2 and then type gksu gedit /etc/fstab and then press enter then put a # in front of any partitions you don't want to use in ubuntu.

Although I'm not entirely sure where to put the #

This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=547f36fa-ddec-4229-a119-7759dace36e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-081E  [COLOR="Red"]#[/COLOR]/media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=866C62066C61F0FB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       [COLOR="Red"]#[/COLOR]/media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=b27ec669-5e76-4dba-8151-a37400d0d4d9 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I need to make sda1 and sda3 go away. Should the # 's be where I've already put them in [COLOR="Red"]red[/COLOR]?

---

### Post by Medieval_Creations on 2007-07-11
> **Tommerz said:**
> Medieval's idea sounds good, just hit alt+f2 and then type gksu gedit /etc/fstab and then press enter then put a # in front of any partitions you don't want to use in ubuntu.
It's a complicated way round it, it may be worth you installing gtweakui through synaptic and doing it that way instead then just creating shortcuts to your drives afterwards :).

Yea, I guess I could been a little more specific on how to go about doing it.
Sorry about that.

> **kevinlyfellow said:**
> Actually, you don't need to install anything, the option is in gconf
```
gconf-editor /apps/nautilus/desktop/volumes_visible
```

That's great to know.  I knew there had to be a way.

---

### Post by Medieval_Creations on 2007-07-11
My guess is it's going to be one of these.  The very first one (sdb1) is an ext3 partition which would be you linux install.

```

#UUID=07D6-081E /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
#UUID=866C62066C61F0FB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

1 of these will be your Windows Install & the other will be the restore image.
Base off the partition types (vfat & ntfs), I would assume that the first (vfat)  is your Restore Image and the other (ntfs) is your Windows Install.  But I'm guessing.  One way to be sure is what file system is your Windows Install setup on.  That could point you in the right direction too.

Worst case trial and error and a couple of reboots.

You' d want the # to be the very first thing in that line.  As seen above.

---

### Post by OliverN on 2007-07-11
> **Medieval_Creations said:**
> My guess is it's going to be one of these.  The very first one (sdb1) is an ext3 partition which would be you linux install.

```

#UUID=07D6-081E /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
#UUID=866C62066C61F0FB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

1 of these will be your Windows Install & the other will be the restore image.
Base off the partition types (vfat & ntfs), I would assume that the first (vfat)  is your Restore Image and the other (ntfs) is your Windows Install.  But I'm guessing.  One way to be sure is what file system is your Windows Install setup on.  That could point you in the right direction too.

Worst case trial and error and a couple of reboots.

You' d want the # to be the very first thing in that line.  As seen above.

Actually, I backed it up first and tried my own idea (#/media/sda1 and #/media/sda3) and that worked! :)

Thank you all who helped.

---

