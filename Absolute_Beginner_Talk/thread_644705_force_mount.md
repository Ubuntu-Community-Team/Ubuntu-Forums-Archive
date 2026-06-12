---
title: "force mount"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by xoli on 2007-12-19
i've got a hard drive that is slowly dying i need to back up my data.my problem is that i can't seem to mount the drive.i've taken a screen shot of the error message that i'm getting.Any ideas on how to solve this?

---

### Post by Pumalite on 2007-12-19
Fix your drive first with Gparted Live CD or TestDisk or Rescuecd

---

### Post by jw5801 on 2007-12-19
Or just call fsck, since that's all the other's will do.
```
sudo fsck /dev/sdb1
```You can use the -N switch to simulate what would be done first if you want.

---

### Post by xoli on 2007-12-19
i've tried this option already no luck. but thanks

---

### Post by jw5801 on 2007-12-19
Did you try ```
dmesg | tail
```to see if there was any useful information. And what happens when you run fsck on the partition?

What filesystem are you trying to mount? Is it NTFS, FAT16, FAT32, EXT3? We can try mounting it from the commandline and see how far we get. The command will depend on what filesystem it is though.
```
sudo mkdir /tmp/mount/
sudo mount -t *filesystem-type* -s /dev/sdb1 /tmp/mount/
```
The -s switch allows for a sloppy mount rather than an outright fail. So it might be useful in this instance.

---

