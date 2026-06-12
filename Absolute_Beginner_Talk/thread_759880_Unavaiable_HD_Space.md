---
title: "Unavaiable HD Space"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by computermesh on 2008-04-19
I have a 300GB Sata HD and I am only available to see 269.4 GB any idea how I can see where the rest went?

---

### Post by Existentialist on 2008-04-19
Around 279GiB is normal for what an OS will report on a 300GB drive due to the different definition of GB (base-10 or base-2).  As for the other 10GB, it is probably due to the ext3 format used, which tends to loose 5-10% when formatting.

---

### Post by quirks on 2008-04-19
You can reduce the 5% reserved by ext3 for the root user using this command:
```
sudo tune2fs -m 1 /dev/your_hdd_device_file
```
This will reduce the reserved percentage to 1%, which should still be enough for a 300GB disk. I did this for my external disk.

[B]Beware:
- Do not run this command, if you don't need to.
- The filesystem must not be mounted.
- You can lose data, if you do something wrong.[/B]

---

### Post by bumanie on 2008-04-19
Drive manufacturers round off numbers when designating their drive capacities. For instance 1mb= 1024 kb - not 1000kb Similarly, 1 gigabyte = 1024 mb, not 1000 mb. However drive manufacturers round the value of 1024 down to 1000, that accounts for much of the 'loss' in storage that you see. Also as rightly stated, once there is a file system on the drive, some of the capacity is reserved for that.

---

