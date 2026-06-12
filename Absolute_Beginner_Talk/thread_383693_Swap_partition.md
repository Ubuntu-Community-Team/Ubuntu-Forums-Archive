---
title: "Swap partition"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Bingo Jesus on 2007-03-13
I'm a happy Ubuntu user for nearly six months now and I think it's time to make the jump to a fully linux machine. I've got a 100GB hard disc and I'm planning on partitioning 50 GB of that for a shared FAT 32 partition, and the rest for a stable release and an experimental release (7.04 etc.)

Is it possible to have a shared swap partition for all versions on linux installed on the machine, and if so how? Many thanks.

---

### Post by taurus on 2007-03-13
Yes, you can use the same swap partition for all versions.  Just mount that partition as swap in each release and you are all set.

---

### Post by Bingo Jesus on 2007-03-13
Thanks, I might do that tomorrow, once all my files have been backed up.

---

### Post by Rotaj on 2007-03-19
> **taurus said:**
> Yes, you can use the same swap partition for all versions.  Just mount that partition as swap in each release and you are all set.

Would this also work on for a machine dual booting with XP and edgy(for now) to share data between the 2 OS's

---

### Post by LanDan on 2007-03-19
> **Rotaj said:**
> Would this also work on for a machine dual booting with XP and edgy(for now) to share data between the 2 OS's

this would have very little to do with a swap partition, but if you would like to have a shared data partion that will be accessible from both linux and windows that is very well possible,  

windows           partion NTFS     10 GB
windows/linux    partion FAT32   50 GB  (storing data only)
swap                partition swap    512MB
linux                 partition EXT3   10GB    (dapper)
linux                 partition EXT3   10GB    (edgy)


just make sure you partition the data partition to a file system both can read and write to, i suggest FAT 32, above is an example offcourse so you can play around to your likings

---

### Post by rusty4r on 2007-03-19
I have five different distros all sharing the same swap. When you install, the gparted program will recognize that you already have a swap file.

---

