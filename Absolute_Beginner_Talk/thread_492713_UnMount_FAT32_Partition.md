---
title: "UnMount FAT32 Partition"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Nommy on 2007-07-05
Hi Everyone,

I recently installed Ubuntu  7.04 (Feisty Fawn) on my PC My PC already have two Fat32 partitions and when I boot from Ubuntu these two Fat32 partitions are automatically mounted and displayed  on my desktop. What I want to know is how can I unmount these two Fat32 partitions although I have never edited my fstab file. I have also commented the entries of these two partitions from fstab file but still these partitions are automatically mounted when ever i boot from Ubuntu.

Please reply ASAP.

Thanks,

Nommy.

---

### Post by Nythain on 2007-07-05
to temporarily unmount them type
```

sudo umount /dev/xxxx

```
replacing xxxx with the appropriate device name of the partition you want to unmount, like sda3 or hda4 or whatever it is on your pc... alternatively you can type the location its mounted at like
```

sudo umount /media/windows

```
if /media/windows was where teh partition was being mounted at

to make it not mount automatically i would have to see your fstab file to see whats goin on there

---

### Post by bodhi.zazen on 2007-07-05
If you do not want the to mount automatically, in the 4th column, change auto to noauto. Add users (if needed) so that users (and not only root) can mount the partition, or not ...

so ..

/dev/hdxy /mount/point vfat **noauto**,users,.... 0 0

---

### Post by Nythain on 2007-07-05
yeah, i was basically gonna see if the fstab was set up with defaults, or if it listed teh options its using, saying replace auto with noauto isnt much help if its currently set to defaults... in that case could change defaults to rw,users,async,exec,noauto... or would just adding ,noauto after defaults work just the same??? my fstab knowledge is still a little weak at the moment

---

### Post by bodhi.zazen on 2007-07-05
> **Nythain said:**
> yeah, i was basically gonna see if the fstab was set up with defaults, or if it listed teh options its using, saying replace auto with noauto isnt much help if its currently set to defaults... in that case could change defaults to rw,users,async,exec,noauto... or would just adding ,noauto after defaults work just the same??? my fstab knowledge is still a little weak at the moment

Well you are on the right track, but the options for fstab are dependent of the type of file system.

So for fat partitions you use umask=007 (or 000) rather then rw.

If you have insomnia you can look at this ....

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

