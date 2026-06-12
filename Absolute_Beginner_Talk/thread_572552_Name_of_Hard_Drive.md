---
title: "Name of Hard Drive"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-10-10
Hello I'm trying to do this tweak and I'm stuck on the last part.

    *  Now we are going to edit the Fstab because it will be expecting these options. 

sudo nano -w /etc/fstab

    * Now you are going to want to add the (data=writeback and noatime=0) flags to your hard drive. It might be a little confusing because of the new naming system. Look for the (,errors=remount-ro) and add it afterwards to make it look like our example. 

defaults,errors=remount-ro,data=writeback,noatime 0

    * Now you tell your system to use them both. 

[B]sudo tune2fs -o journal_data_writeback /dev/yourdrive
[/B]

What is "yourdrive", I dunno what I should put in it.

```
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: No such file or directory while trying to open /dev/yourdrive
Couldn't find valid filesystem superblock.

```

---

### Post by Vixis on 2007-10-10
It must be something like /dev/hda1
you may see it in /etc/fstab, where you added flags

---

### Post by P4rD0nM3 on 2007-10-10
Cool. THANKS.

---

