---
title: "please tell me how to dual-boot ubuntu 7.04 on my Windows XP tottoed PC?"
date: 2007-09-28
forum: Arizona Team - US
---

### Post by yawmosh on 2007-09-28
I am an absolute beginner.I HAVE  a Compaq  PC with HP sofware installed on local disk D and Windows XP installed on the disk C from the factory.I tried to dual boot Ubuntu 7.04 on it but my computer refused and displayed this message ,while coming on partitioning the disk;

How do you want to partition the disk?

1/Erase entire diskSCSI1(0,0,0)(sda)-100.0GB ATA ST9100824AS

2/Manually edit partition table.

I don't know anything about manual partition.Pllease help me:(:(:(:(

---

### Post by pay on 2007-09-28
You need to create 2 partitions (or more if you wish). The first partition needs to hold you installation. Create it with ext3 and mount point "/" (don't add ""). Make this partition as large as you want but atleast about 5gb. Next you need a swap partiton. The general rule is to make it twice the size of the amount of ram you have .

You can add other partitions but those 2 are the essential ones.

---

