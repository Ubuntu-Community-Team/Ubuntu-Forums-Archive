---
title: "Second SATA HD is split into sda1 and sda5 despite being one partition - why?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by phucough on 2006-12-25
So I installed a SATA drive into my computer. At first it was formatted as NTFS in Windows, but I went into Ubuntu and used cfdisk to create one logical partition on it, which is currently set up as ext3, although I am yet to mount. However, typing in

```
sudo fdisk -l
```

Yields this information for the second drive:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    5  Extended
/dev/sda5               1       38913   312568609+  83  Linux

```

Why is it split into sda1 and sda5, even though there's only one partition set up on the computer? And is there any way to stop this?

Thanks in advance for any help, and a Merry Christmas to you!

---

### Post by logos34 on 2006-12-25
sounds like you confused logical with PRIMARY partition...one big primary is what you want

---

### Post by phucough on 2006-12-25
My first (IDE) hard drive is the primary partition, I'm going to mount this drive in /media.

I set it up as primary before by accident and the same thing happened, two partitions (sda1 and sda5) that use the same drive space (???), so that isn't it.

---

### Post by phucough on 2006-12-25
Oh yeah, when I go into cfdisk it only shows the sda5, not sda1.

---

### Post by phucough on 2006-12-25
> **logos34 said:**
> sounds like you confused logical with PRIMARY partition...one big primary is what you want

Hang on, I checked and you're right. When I made it primary before, I forgot to actually write it ](*,) 

Thanks!

---

