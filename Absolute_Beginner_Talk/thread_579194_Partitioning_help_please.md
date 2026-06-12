---
title: "Partitioning help please"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by cdog on 2007-10-18
hello all,

I'm a very new user of Linux & thus Ubuntu, love it btw. Have run into trouble whilst enlarging my filesystem partion. Used Gparted to do the work, yet could not complete all operations due in part to  the partition be mount after being resized. Could not run fsck. I have since done this manually, yet I now have a 20.97Gb drive, but my filesystem only recognizes it as the previous 7.9Gb drive. Gparted tells me it is 20.97Gbs, as does windows....How do I get my filesystem to do the same ???

any ideas would be much appreciated....thx

---

### Post by hyper_ch on 2007-10-18
Use the live cd for altering the partitions. They must not be mounted while you work on it.

---

### Post by cdog on 2007-10-18
Yeah did that.........however the partition mounted automatically after being created with the live cd. My system works fine, I just want the filesystem to tell me it has heaps more free space than the current 1.3Gb

what did I miss ...??

---

### Post by hyper_ch on 2007-10-18
Then you have to unmount the partitions first

```

sudo umount /dev/hdX

```

replace hdX with the according devices.

---

### Post by cdog on 2007-10-18
thx hyper_ch

went back to the live cd, made the partition smaller, then larger again......worked fine this time & filesystem is now recognizing the free space.......thx for the help

---

### Post by hyper_ch on 2007-10-18
you're welcome.

---

