---
title: "best way to increase partition for current linux install"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-05
Recently had to reinstall xp. I installed xp then ubuntu but i thought i was giving ubuntu 100 gigs.. Well it ended up being ubuntu 20 gigs and xp 100gigs.. So i need to reverse that..i have xp and ubuntu on the same hard disk.. Need to keep xp due to gaming and few applications that only work in windows.. So how would i go about resizing the ubuntu partition?

---

### Post by adam.tropics on 2006-06-05
Try the partition manager off the live cd. I just resized an xp partition from it with no problems at all.I always worry a bit about messing with partitions though so backup anything imoportant first just in case!

---

### Post by GarethMB on 2006-06-05
gparted.

It's in  the repos

```
sudo apt-get install gparted
```

---

### Post by lime4x4 on 2006-06-05
ok got it installed but when i click on the linux partition it doesn't give me the option to resize

---

### Post by bruenig on 2006-06-05
Load the live cd. Go to System>Administration>Gnome Partition Editor. Resize the Windows partition, make sure the extra space is adjacent to your ubuntu partition (i.e. If windows is first make sure the newly created extra space is after the windows partition, the opposite if windows is second). After that resize the Ubuntu Partition to take up the rest of the remaining space. Apply changes, reboot and remove the live cd.

---

### Post by lime4x4 on 2006-06-05
okay this is what i ended up with
sda1 20 gigs windows xp
sda4 57 gigs ext3
sda2 37 gigs ubuntu
sda5 1.5gigs linux swap file

When i try to resize sda2 it's already telling me it's at the max size now it won't use the 57 gigs that's before it

---

### Post by az on 2006-06-05
You need to copy it to there, delete the original and then extend it.  You cannot resize by moving the start of a partition, only the end.

---

