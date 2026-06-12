---
title: "Drive icons that should not be on desktop"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-11-27
I have two mdadm arrays, and they are mounted like this in /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=6257b146-1962-4028-8b45-f4e79592bb7f /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback  0 1
# /dev/sda1
UUID=751e518b-6b02-4e9c-99a5-3f6137c43f1c /boot           ext2    defaults        0       2
# /dev/sda2
UUID=964e1e38-c685-41fd-9520-0f56cd1e5d24 none            swap    sw              0       0
# /dev/sdb1
UUID=1adc7a14-bb7c-465e-8cdb-f642fdbc6a3d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#
# /dev/md1
UUID=33f2638c-f8da-4494-8337-be8b5d11f34e  /home/bob/Data1  ext3  defaults,user,noatime,nodiratime,data=writeback  0 2
```

That last one, /dev/md1 shows up now on my desktop as Data1.. but never used to do so before.  Is there something I can change in fstab or elsewhere to prevent the icon from appearing?  I like a clean desktop (Gnome) with nothing there that I didn't put there for a reason.  I find this drive icon annoying, but can't seem to get rid of it.  I've tried auto, and a bunch of other things, but nothing seems to get rid of it.

Thanks,
Bob

---

### Post by the yawner on 2007-11-27
Hi, have you tried running gconf-editor? It has a settings there that can prevent volume icons from appearing on the desktop. Just follow apps>nautilus>desktop and uncheck the option volumes_visible.

---

### Post by RTrev on 2007-11-27
> **the yawner said:**
> Hi, have you tried running gconf-editor? It has a settings there that can prevent volume icons from appearing on the desktop. Just follow apps>nautilus>desktop and uncheck the option volumes_visible.

That worked, but now I have no icons for things like USB sticks, which I find helpful.  I'd like insertable media to show up, but not my normal internal drives.  Any way to do that?  There must be because in my previous installations that was the default behavior.  I can't figure out what changed from my last Gutsy install to this one.  :confused:

But thanks, I prefer to have no drive icons than have that permanently mounted drive showing up there all the time.

Bob

---

