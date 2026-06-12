---
title: "Can't see my hard drive"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Lampros G on 2006-12-02
Hello there,

I have the ubuntu 6.06 LTS live cd for the pc. I'm booting it from the cd and I'm trying to install it in my hard drive. The thing is, it can't see my hard drive at all. I put a usb flash drive and it sees it. I tried creating a partition with norton partition magic and I formatted it in ext3. Still can't see anything. Can someone help me with this?

I have a SATA hard drive with 5 partitions from which the one is ext3. The partitioning of the disk is made by the windows install cd..

My mainboard model is 775Dual-VSTA.

And my chipset says:
Northbridge	VIA PT880 Pro rev. 00
Southbridge	VIA VT8237A rev. 00

---

### Post by Chinkostu on 2006-12-02
you'll need to load the SATA drivers i think, unfortunately i've had no experience of SATA so i can't say how. 6.10 (edgy) detects SATA drives straight away from what i've read.

---

### Post by agonoruci on 2006-12-02
ya it is supposed to, What manufacturer is your hard-drive.

---

### Post by Lampros G on 2006-12-02
I'll download 6.10 and see what happens :)

---

### Post by Lampros G on 2006-12-02
I'm getting the informatin from cpuz. The only thing I can read is that the BIOS Vendor is American Megatrends Inc.

---

### Post by bodhi.zazen on 2006-12-02
Boot to the live CD

To list your partitions, In a terminal type:```
sudo fstab -l
```

If you post the output we can help.

Also try launching gparted....

---

### Post by Lampros G on 2006-12-02
I can't seem to manage the command, it says it doesn't undestand it or something.. (Remember I'm brand new at this)

GParted can't see any partitions..
I'm currently downloading the ubuntu 6.10 to see if that's going to help me..

---

### Post by bodhi.zazen on 2006-12-02
> **Lampros G said:**
> I can't seem to manage the command, it says it doesn't undestand it or something.. (Remember I'm brand new at this)

GParted can't see any partitions..
I'm currently downloading the ubuntu 6.10 to see if that's going to help me..

Error message?

That is a small "L" and not the number 1.

```
sudo fstab -l
```

Should list all your partitions....

---

### Post by Lampros G on 2006-12-02
Ubuntu 6.10 worked and now I can see my partitions. The problem is now where I'm suposed to mount the partitions. I selected one root partition ("/") and one for swap. The message says that there is no root file system..

---

