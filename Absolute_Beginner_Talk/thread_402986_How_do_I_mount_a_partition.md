---
title: "How do I mount a partition?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
I want to access my other partitions.

How do I mount a partition?

After mounting a partition, will I be able to edit files from other partitions?

Edit:

I found out how I am supposed to mount partitions.

What I do not know now is how I can edit files from other partitions and how I can permanently mount partitions, meaning, when I boot, partitions are automatically mounted.

---

### Post by dr.silly on 2007-04-06
get this piece of software [http://getautomatix.com/](http://getautomatix.com/) and it should have one called automatically mount check it to install

---

### Post by szymon_g on 2007-04-06
is that windows partition (ntfs/fat32)?

---

### Post by theninthdimension on 2007-04-06
Wersdaluv,

     You may want to check out the directions in this post ([http://ubuntuforums.org/showthread.php?t=402062](http://ubuntuforums.org/showthread.php?t=402062)) before installing other software. These instructions should work. If not, let me know.

Jeff.

---

### Post by xerox on 2007-04-06
I just learned this, and it works for me.

Open your Terminal (Applications>Accesories>Terminal), then type the following commands.  (Substitute "hda1" for your partition number or name.)


sudo mkdir /mnt/hda1 (make somewhere to mount to)
sudo mount /dev/hda1 /mnt/hda1


That's all! Afterward, you should be able to access your partition from Places>Computer>Filesystem>mnt

---

### Post by wersdaluv on 2007-04-06
Thanks guys, but what I want to mount is another Linux partition.

---

### Post by Happy_Man on 2007-04-06
Same thing as what xerox said, then.

---

### Post by finer recliner on 2007-04-06
should work the same way as xerox explained

---

### Post by wersdaluv on 2007-04-07
What if I want another Linux partition to be permanently mounted?

I noticed that, when I reboot, the mounted partition will be unmounted.

---

### Post by finer recliner on 2007-04-07
look here: [https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html)

remember your mounting an ext3 partition, not ntfs. should be nearly the same

---

