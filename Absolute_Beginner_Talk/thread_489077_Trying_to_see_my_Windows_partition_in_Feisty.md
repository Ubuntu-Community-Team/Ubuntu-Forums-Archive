---
title: "Trying to see my Windows partition in Feisty"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-07-01
Hey everybody,

I installed NTFS support using Automatix2.  At first it showed my 49 gig windows partition, but when I rebooted it was gone.  I looked in the mount folder, but I could have sworn it was in the "computer" folder.  Anybody have any idea what could have happened?  Did Feisty not remount this partition, or do I have do that manually every time I want access to my windows files?

Thanks,

Helixed

---

### Post by logos34 on 2007-07-01
In a terminal type these three commands:
[B]
sudo fdisk -l [/B]
(i.e. lowercase L)

**mount**

**cat /etc/fstab**

Post the output.

---

### Post by helixed on 2007-07-07
Well, it's weird, but when I restarted Ubuntu again, the OS suddenly seems to be able to read my partition.  I can't really figure out why this is, but after several more restarts it's still there.  I guess I'll post back if I have this problem again.  Thanks for the help.

Helixed

---

### Post by rookshop on 2007-07-07
I had the same problem. After typing the three statements I got the following output:

#Entry for /dev/sda3 :
UUID=e322ccbd-772e-4bde-81e6-0ac5278638d / ext2 defaults, errors=remount - ro 0 1

Have no clue what this means.... :)

---

