---
title: "Resizing Partition: Formatting Required?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-12-10
I have Kubuntu 6.06 installed along with Windows XP.

Currently I have 3 major partitions:

30 GB NTFS  (Windows)
40 GB ext3  (Linux)
10 GB FAT32 (Shared)

I want to expand the 10GB shared to 20GB by taking 5GB from each of the other two partitions.... so that I can put all my media in it which I can access via both OSes.

Now, if I were to use GParted (or anything else) to reduce the size of the NTFS/ext3 partitions and increase the FAT32, will it require me to format it? I really don't want to do that, as there will be a lot of data to backup.

---

### Post by Crakie on 2006-12-10
I am pretty sure you wont have to reformat. A backup is still a good idea though, as these kind of operations have a (small) chance of going wrong.

Also, you can only take space from partitions that are physically next to the one you are expanding. So if the order on your drive is as you listed, you need to take 10 Gb from the ext3 and then give 5 Gb from it to the NTFS.

---

### Post by slimer on 2006-12-10
PartitionMagic

---

### Post by KuriKai on 2006-12-10
PartitionMagic screws up ext3 partitions

---

### Post by carloslosgrande on 2006-12-10
Hi Verminox.
I recently re-partitioned all my previous partitions with GParted. Its ****-hot. You don't need to worry about formatting. as Crakie says - doing a backup is always a good idea with this but I had absolutely no trouble and I need REALLY simple things. You'll see what you are able to do graphically so it'll be very clear, basically you'll have do follow Crakie's advice > Also, you can only take space from partitions that are physically next to the one you are expanding. So if the order on your drive is as you listed, you need to take 10 Gb from the ext3 and then give 5 Gb from it to the NTFS.

---

### Post by Verminox on 2006-12-10
Thanks.

My actual order is:

hdc1 - ntfs - 29.30 GB
hdc2 - extended - 11.21 GB:
-- hdc5 - fat32 - 9.77 GB
-- hdc6 - linux-swap - 1.44GB
hdc3 - ext3 - 34.05GB


I'll be able to take 5GB from NTFS to FAT32... but what about ext3?

Any idea how I would go about doing it?


Edit: Will I have to do this through the LiveCD or directly through Kubuntu? Because wouldn't resizing ext3 give problems as Kubuntu is on the ext3 partition!

---

