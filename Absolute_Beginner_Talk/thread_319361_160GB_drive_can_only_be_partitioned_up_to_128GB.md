---
title: "160GB drive can only be partitioned up to 128GB"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by feap on 2006-12-15
I can only see 128GB in gparted and administration/disc, although the HDD I'm installing is 160GB. The 2.5" HDD is in an external Hyperdrive SPACE enclosure. Any partition system setup doesn't show that the drive has more than 160GB - ie. i can make a 100GB partition and be left with only 28GB.

The HDD is a brand new Samsung SpinPoint M60 (model # HM160JC) and works otherwise wonderfully.

Note: this is a follow-up to the following thread which has been solved: [http://www.ubuntuforums.org/showthread.php?t=319281](http://www.ubuntuforums.org/showthread.php?t=319281)

---

### Post by gn2 on 2006-12-15
Do you have large hard drive supported in your BIOS?

---

### Post by lyceum on 2006-12-15
Wow! I have never had this problem, but...

Did you try installing anything else to see if it is the hard drive rather than the disk (Ubuntu)? I would try a Windows disk (if you have one) or stand alone partison program. If you can get to fdisk to check, all the better.

---

### Post by feap on 2006-12-15
My BIOS has no options to turn large drive support on/off.

I don't have access to a Windows computer. I've used both fdisk and gparted to try to partition larger than 128GB, same problem :(

---

### Post by Fatec on 2006-12-15
> **feap said:**
> My BIOS has no options to turn large drive support on/off.

I don't have access to a Windows computer. I've used both fdisk and gparted to try to partition larger than 128GB, same problem :(

Just to clarify something here, when you buy a 160GB you dont get 160GB anyway, it will be around 130-150GB (depending on the brand)...so maybe that's why its only showing as 128GB...or as mentioned before, could be a bios restriction in which case you may need to flash your bios.

---

### Post by lyceum on 2006-12-15
> **feap said:**
> My BIOS has no options to turn large drive support on/off.

I don't have access to a Windows computer. I've used both fdisk and gparted to try to partition larger than 128GB, same problem :(

This sounds like a hardware problem. Hate to seem helpless, but I would take it back and get a new one. Someone here may know something else, but if fdisk says 128 it is 128 as far as I know.

---

### Post by That_Geek on 2006-12-15
yes, either the BIOS wont support it or, that is just how big it is in reality

---

### Post by feap on 2006-12-15
I'm aware that GB for hardware manufacturers is not 1024MB (it's 1000MB), but even then it should be around 150GB.

---

### Post by Fatec on 2006-12-15
> **feap said:**
> I'm aware that GB for hardware manufacturers is not 1024MB (it's 1000MB), but even then it should be around 150GB.

Well...as i said, really depends on the brand, i've had a 160gb and it weighed in at 120gb before.

Though its un-usual..but yes.

Anyways...if your sure that it should be 150gb (well, 148 to be exact)

then you need a new bios update.

---

### Post by gn2 on 2006-12-15
This was a common problem in Windows, and was fixed by switching to 48-bit Logical Block Addressing. (LBA)

The last time I encountered it was recently when I built a W2kPro machine for a friend with a Western Digital 160Gb drive. It showed 128Gb until I fixed it.

How you do this in Linux I don't know.

What file system have you partitioned the drive as, and did you make it primary or logical?

Is there 48-bit option in partitioning utility?

---

### Post by feap on 2006-12-15
I partitioned it using fdisk in Ubuntu terminal. Both fdisk and gparted show only 128GB availalbe.

I think the issue might be BIOS. The notebook is Compaq Evo N610c and the BIOS doesn't have an option for LBA or large drives. I guess I'll just wait till I get to my desktop and reformat it then to full size.

update: found the culprit. Hyperdrive SPACE (the external HDD housing) has a setting for 48-bit LBA which had to be turned on to enable larger than 128GB sizes. So all is well :)

Thanks again for all the help!

---

### Post by moshuptrail on 2006-12-15
gn2 is correct.  If you don't have LBA support in the bios, you will only be able to use 128Gb - even if you had a 500Gb HD.

---

