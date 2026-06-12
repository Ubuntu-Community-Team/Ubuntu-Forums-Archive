---
title: "Installing ubuntu fiesty"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by dummyhead3 on 2007-09-15
Hi, 
I just got this new computer with windows home basic preinstalled, so as this sucks, I've decided to install ubuntu, but I'm not ready to say goodbye to Windows. I want to dual-boot ubuntu and windows vista home basic. Here are some specifications about my desktop:

AMD Athlon 64 +3600
1 GB DDR2 memory
160 GB SATA hard drive
GeForce 6100 nForce 405 integrated graphics card

I have a (Live) CD with ubuntu 7.04 on it. I have four partitions on my hard disk:

/dev/sda1    mountpoint: media/PQSERVICE     size: 9.76 GB
/dev/sda2    mountpoint: media/ACER              size: 71.95 GB   flag: boot
/dev/sda3    mountpoint: media/DATA              size: 66.68 GB
/dev/sda4    mountpoint: media/disk               size: 5 GB

All the partitions use ntsf as the file system. The first one is the configuration partition, which I can't see in windows (I am currently using the live CD), the second one is the place for basically everything else, the third one is a free partition, finally the last one, I freed up some space from the DATA and made another partition for the swap file. I want to use DATA to install ubuntu. Can you please guide me through the step 4 of the install, I really don't wanna loose windows...

---

### Post by mikewhatever on 2007-09-15
The partition intended for Ubuntu must be mounted as /, and the one for swap as swap. Do not mount them in media as the above shows. Look at the pictures:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by dummyhead3 on 2007-09-15
But... is it gunna change file system by itself?

---

### Post by mikewhatever on 2007-09-15
No, you have to specify the file system. Look at the pictures of the guide. Since you've already created the required partition, highlight sda3 and click Edit partition. Specify ext3 file system and / mount point. For sda4 put swap in filesystem, and the mount point option should be grayed out.

---

### Post by dummyhead3 on 2007-09-15
which one would should i choose then

---

### Post by HereInOz on 2007-09-15
You would use ext3 for your system partition, and if you make a separate /home partition, and then you would choose swap for the swap partition.

---

### Post by dummyhead3 on 2007-09-15
WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

what do they mean by "any partitions you have removed"

---

### Post by mikewhatever on 2007-09-15
> **dummyhead3 said:**
> which one would should i choose then

Look at the screenshot [http://img264.imageshack.us/img264/9426/feistydual12xc2.png](http://img264.imageshack.us/img264/9426/feistydual12xc2.png)

---

### Post by dummyhead3 on 2007-09-15
WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

what do they mean by "any partitions you have removed"

---

### Post by HereInOz on 2007-09-15
I means that if you have selected any partitions which you want the partitioner to remove, it will destroy all the data on it.

Example:  Your current HDD probably has one partition on it - the Vista one.  If you told the partitioner to remove that partition, it would happily do so and you would lose the lot.  the idea is to re-size the Windows partition smaller so that you have free space on the drive, and then create the appropriate partitions in that free space.

---

### Post by st33med on 2007-09-15
He means that if you want to recover data off of that deleted partition after formatting, it won't be able to because it is all erased.

---

### Post by dummyhead3 on 2007-09-15
I didn't touch those partitions so im OK...

---

### Post by st33med on 2007-09-15
I forgot to mention:
If you format it, you will loose all of your data

---

### Post by dummyhead3 on 2007-09-15
Thanks, just installed it, works OK.. as far as I know and windows is still there

---

### Post by mikewhatever on 2007-09-16
> **dummyhead3 said:**
> Thanks, just installed it, works OK.. as far as I know and windows is still there

Congratulations, we are all delighted.

---

