---
title: "GrubError 5?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ShawnTRD on 2007-05-08
Every time I try install a third SATA hard drive I get a error when loading grub. 

Error 5

The drive isn't even partitioned.  Any ideas?

---

### Post by ShawnTRD on 2007-05-08
XP on first drive

Ubuntu 7.04 on the second drive

---

### Post by confused57 on 2007-05-08
> **ShawnTRD said:**
> Every time I try install a third SATA hard drive I get a error when loading grub. 

Error 5

The drive isn't even partitioned.  Any ideas?

See the description & possible solution  for grub error 5:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors)

---

### Post by Qchan on 2007-05-08
[b][color=darkred]
When you plug that in your PC, depending on how the jumpers are set on the HDD, it can switch around the locations of where your HDDs might be. (I.E. SDA1, SDA7). Make sure the new HDD's jumpers are correctly set. If you already have a master drive installed, then set the new HDD to slave. That'll fix your problem.
[/b][/color]

---

### Post by confused57 on 2007-05-08
Good advice from Qchan, but you might also want to check your hard drive boot order in bios...the one with grub(Windows?) would be first, followed by the Ubuntu drive, then the new drive.

---

### Post by ShawnTRD on 2007-05-09
> **confused57 said:**
> Good advice from Qchan, but you might also want to check your hard drive boot order in bios...the one with grub(Windows?) would be first, followed by the Ubuntu drive, then the new drive.

I tried this with no luck.

---

### Post by ShawnTRD on 2007-05-09
> **Qchan said:**
> [b][color=darkred]
When you plug that in your PC, depending on how the jumpers are set on the HDD, it can switch around the locations of where your HDDs might be. (I.E. SDA1, SDA7). Make sure the new HDD's jumpers are correctly set. If you already have a master drive installed, then set the new HDD to slave. That'll fix your problem.
[/b][/color]

SATA has no Slave/Master settings

---

