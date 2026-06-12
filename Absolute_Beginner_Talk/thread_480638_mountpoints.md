---
title: "mountpoints"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-21
I just installed ubuntu 7.04 and have 2 hd's.  I originally removed my 30 gb slave and replaced it with a 40 gb. I formatted the 40 gb in ext3 and combined two partitions using gparted.  However, I am unable to see the new hd like I did the old hd when it was in place.  I plan on using the 40 gb for storage. Do I need to change mountpoint or what?  Thanks.

---

### Post by Skrynesaver on 2007-06-21
Try the following
```

sudo mkdir /mnt/hdb1
sudo mount -t /dev/hda2 /mnt/hdb1

```
If that works, then you can add the partition to the /etc/fstab file.
To do this properly you should really get the vol_id
```

sudo vol_id /dev/hdb1

```
Then add the following line to your fstab
```

UUID=<The value gained above> /Storage         ext3    defaults        0       2

```

---

### Post by nidoo on 2007-06-21
Hi GUDDR,

I has a similar problem with my slave IDE HDD, and the friendly people here helped me, I think it will also work for you.

First 

To see where your HDD partition is located use the command -
> sudo fdisk -l

Second
Create a directory for the new HDD with -
> sudo mkdir /media/sdb1

*.* sdb1 is what my slave is i'll assume it's the same for you

Third

To mount it you can either do it by hand by the command -
> sudo mount -t ext3 /dev/sdb1 /media/sdb1

or to mount it everytime by adding the following line to /etc/fstab -
> /dev/sdb1 /media/sdb1 ext3 defaults 0 2

I hope this helps. :D

---

### Post by guddr on 2007-06-21
Thank you all for your help.

---

