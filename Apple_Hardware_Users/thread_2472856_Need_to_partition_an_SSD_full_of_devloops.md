---
title: "Need to partition an SSD full of /dev/loops"
date: 2022-03-15
forum: Apple Hardware Users
---

### Post by tahitiwibble on 2022-03-15
Hello to one and all, I'm stumped.

Trying to install 20.04 on an old MacBook Air for a friend and on her drive I have found something very similar to this;

```
sudo fdisk -l

Disk /dev/loop15: 3.7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 54.6 MiB, 57274368 bytes, 111864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

My problem is that using Gparted from a live USB drive I can't see **any** partitions to work with.

How can I get rid of all these 'loops' and be able partition the SSD so as to install 20.04?

---

### Post by ActionParsnip on 2022-03-15
Are you intending to have Ubuntu as the only OS on the system? If so then simply tell the installer to use the entire disk

---

### Post by yancek on 2022-03-15
The link below gives a basic explanation of what the /dev/loop is.  Nothing unusual about it.  

[https://linuxhint.com/dev-loop-linux/](https://linuxhint.com/dev-loop-linux/)

You don't appear to have any existing partitions   With GParted, you can try going to the Device tab and creating a new partition table and then creating partitions/filesystems.

---

### Post by tahitiwibble on 2022-03-15
> **ActionParsnip said:**
> Are you intending to have Ubuntu as the only OS on the system? If so then simply tell the installer to use the entire disk

Ubuntu will be the only system. Alas, where I would normally be able to partition to accommodate / and 'Home' there is nothing available to partition or configure. The installer has nothing to work with. The whole SSD has become invisible and apppears to have been 'usurped' by these loops.

---

### Post by tahitiwibble on 2022-03-15
> **yancek said:**
> The link below gives a basic explanation of what the /dev/loop is.  Nothing unusual about it.  

[https://linuxhint.com/dev-loop-linux/](https://linuxhint.com/dev-loop-linux/)

You don't appear to have any existing partitions   With GParted, you can try going to the Device tab and creating a new partition table and then creating partitions/filesystems.

In Gparted the only Device available to work on is the live USB drive with 20.04 on it. Not a trace of the SSD to be found anywhere. The SSD is invisible and the total space that the loops occupy corresponds to the space on the drive.

---

### Post by slickymaster on 2022-03-15
*Thread moved to **Apple Hardware Users**.*

---

### Post by tahitiwibble on 2022-03-15
> **slickymaster said:**
> *Thread moved to **Apple Hardware Users. "Please mark your thread as solved if you get a satisfactory response"**.*

I certainly will do, and thanks for moving my question to the Mac sub-forum, I didn't see that that existed.

---

