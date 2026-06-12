---
title: "partitioning and formatting USB-HD"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by KhaaL on 2006-08-04
Hi guys

I wonder how to partition and format an external HD drive? The detection is OK (It shows up as sda) so that is one headache I don't have to worry about

Also, please give me suggestions on what filesystem I should use for maximum crosss-compability (between windows xp and linux mainly). I was thinking about NTFS since linux has a working NTFS driver now, but I haven't managed to install it yet... can ext3 be read and written in windows? FAT32 is out of the question due to the filesize restrictions.

Thanks in advance!

---

### Post by patrick295767 on 2006-08-04
> **Khalid Rashid said:**
> Hi guys

I wonder how to partition and format an external HD drive? The detection is OK (It shows up as sda) so that is one headache I don't have to worry about

Also, please give me suggestions on what filesystem I should use for maximum crosss-compability (between windows xp and linux mainly). I was thinking about NTFS since linux has a working NTFS driver now, but I haven't managed to install it yet... can ext3 be read and written in windows? FAT32 is out of the question due to the filesize restrictions.

Thanks in advance!

vfat32 or ext3 is great for us linux
 
```
sudo apt-get -f -y install qtparted gparted
```

no gui:
or fdisk or cdisk

---

