---
title: "gparted won't let me unmount or resize"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by AlexLinuxUser101 on 2008-02-12
I deleted my windows partition, but i don't know how to use that new space for my main ubuntu partition.  How do I resize the ubuntu partition so that I can use the new space?  I tried unmounting the drive, but I got this error - 

Could not unmount /dev/sda3
The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually

Can someone please give me some guidance so I don't destroy my ubuntu or my computer?  Thanks a lot.

---

### Post by phr0ze on 2008-02-12
Try to download the Gparted boot CD and run it from there. I know its not an ideal solution, but it should work.

---

### Post by oedha on 2008-02-12
gparted will help :==> [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
but you can work on the partitions at step 4 of 7 from ubuntu installation steps
since you have deleted windows partition.....

---

### Post by Rocket2DMn on 2008-02-12
You cannot unmount your root partition while it's in use - that's why you need to use the LiveCD or the GParted LiveCD.  Also, messing with partitions is potentially dangerous, so you should always have complete and up-to-date backups before you proceed with resizing.

---

