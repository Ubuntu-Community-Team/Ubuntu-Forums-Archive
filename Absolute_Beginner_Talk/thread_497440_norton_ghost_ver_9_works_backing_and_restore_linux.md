---
title: "norton ghost ver 9 works backing and restore linux"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by sdowney717 on 2007-07-10
I have a dual boot system with XP and ubuntu.
I used to triple boot xp, ubuntu, fedora.

From the xp, I was able to easily backup and totally restore linux partitions which were stored on my windows partition.
So people who say it does not backup linux partitions are WRONG.

The only thing I ran into was resizing, all restored partitions restored to the same size they were originally, meaning they would not expand if restored into a larger unallocated free space on the drive.
There were no boot issues. XP was the hd0 and grub was on the MBR.

I was able to take partition images and restore them into unallocated space without reformatting for linux. And it worked seamlessly.

Can anyone tell me about the resizing and getting linux to recognize the large space when restored to larger unallocated space?

---

### Post by Maxtorm on 2007-07-10
You can use
```
sudo parted
```
but (a) I'm not sure if you can use it on a live partition and (b) if you make a mistake with parted, you might be up the crick.

A better alternative is using the live GParted CD.  See: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

