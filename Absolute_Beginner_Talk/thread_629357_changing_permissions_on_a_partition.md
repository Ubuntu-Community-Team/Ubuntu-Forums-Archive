---
title: "changing permissions on a partition"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-12-02
Ok long story short: I screwed up the partitions when I installed Linux, I made Vista the main hard drive and Linux the smaller one, and what I wanted to do was the opposite.

I tried to shrink the Windows partition down to 20 GB using the Vista partition editor, but it would only let me shrink it to like 75 GB.

So then I used gparted, and that wasnt letting me resize certain things, so I just formatted two of the partitions to ext3 (assuming this essentially erased Vista as well). One was the main Windows partition (120 GB), the other was the Windows recovery partition (10 GB).

Question 1: is there any way to combine these two partitions into one? no big deal if I cant, it would just make things neater.


My **problem** is that the partitions' permissions are f'ed up. I managed to change the permissions on the 10 GB one by typing sudo chmod 755 (and later changing it to sudo chown 1000). However, when I do that on the 120 GB partition, nothing happens.

I typed this command in terminal:

```
sudo fdisk -l /dev/sda3
```

and got the following output:

```
Disk /dev/sda3: 129.7 GB, 129753792000 bytes
255 heads, 63 sectors/track, 15775 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda3 doesn't contain a valid partition table

```

whats the deal here?

(sorry for posting a second thread related to this, but the theme sort of changed a little)

---

### Post by logos34 on 2007-12-02
no, you want to do 

sudo fdisk -l

(--> shows all the partitions on all the hard disks)

Use gparted to delete the two partitions and then create a single new ext3 taking up the vacated space.

Adding an fstab entry with the correct options should solve your access problems.  See [this guide]("http://www.psychocats.net/ubuntu/mountlinux").  If 'defaults' doesn't do it, try chmod 777.

---

### Post by KevNice on 2007-12-03
cool, that was easy. seems to work fine now.

thanks!

---

