---
title: "Mounting NTFS partitions"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by geezerone on 2006-10-01
Hi

I have seen some threads on this but still having problems mounting a second hard drive with NTFS that wasn't in system during Ubuntu install.

I have installed the following line to the /etc/fstab file and tried sudo mount -a but no joy. 

/dev/hdd1       /media/hdd1     ntfs    ro,defaults,umask=0222 0 0

Any ideas?  Thanks :)

---

### Post by Kateikyoushi on 2006-10-01
What's the output of this command ?

```
sudo fdisk -l
```

---

### Post by jaboua on 2006-10-01
Do you get any error when you run "mount -a" or "mount /dev/hdd1" ?

---

### Post by geezerone on 2006-10-01
Got it sorted. I created /media/hdd1/ directory (sudo mkdir /media/hdd1) and mount -a. Performed reboot to see the new partiton now on desktop. If I wanted to move the partitions to a folder on home for instance so not on desktop would it be straightforward?

Thanks for taking the time to respond! :KS

---

### Post by Kateikyoushi on 2006-10-01
You can move it anywhere you like, just create the directory and change the mount options.
It is not on the desktop that's just a "shortcut", it will stay there even if you change the mount directory, you can remove it tough.

---

### Post by haxer on 2006-10-01
Please try to search i posted this whole thing yesterday!!! :twisted:

---

