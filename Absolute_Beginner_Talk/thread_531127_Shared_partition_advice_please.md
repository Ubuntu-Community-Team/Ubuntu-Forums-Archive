---
title: "Shared partition advice please?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by ergo_emm on 2007-08-21
Hi all, I just got a new laptop and want to make it a dualboot Vista/Ubuntu 7.04 (I really wanted XP, but I can only find upgrade copies around my house and don't want to install Win98 first, heh). I've never done an Ubuntu install before, but I've been looking around on the forums and figure I'll resize my Vista partition from Vista and put Ubuntu in the unallocated space since that seems to be the consensus. I'm currently defragging my harddrive to make sure I have the most free space possible before I make the new partition, but right now my partition info looks like this:

C:\: 140.82 GB total space, 116.88 GB free (which, what the hell, that's ALL Vista because I haven't saved or installed anything)
HP Recovery (D:\): 8.23 GB total space, 1.28 free

I'm thinking I probably shouldn't delete the HP Recovery partition (or should I?), so that leaves me with 140.82 GB to deal with. I really want to use Ubuntu most of the time since in the 12 hours I've interacted with my new laptop Vista's already annoying the hell out of me, so I'm wondering about the best way to partition my HD for me. 

I was thinking I would do a smaller Ubuntu partition (maybe 15 or 20 GB?) and have the rest be shared between Vista and Ubuntu. How is the best way to go about this? I've seen on the forums that if I make a partition and format it as Fat32 that it should just work but that for an NTFS drive, you must use ntfs-3g, and I've seen that some people say ntfs-3g can corrupt your data. How likely is ntfs-3g to do this? I'd really prefer ntfs over fat32, and since I've seen people saying that the ext3 driver doesn't work too well in Vista I don't think I want to go that route. 

Also, I have an NTFS-formatted external harddrive (usb). Will it be difficult to use with Ubuntu?

This got long... thanks for reading!

---

### Post by Hobo Joe on 2007-08-21
It would be better if you just had two partitions for Ubuntu(well, 3 if you count swap), and had 1 be for the OS, and the other for your home folder. If you want to access it from Vista than you can get a driver for that.

I'd say about 8-10 GB for the OS, and about 50GB for the home folder(or more, depending on what you're going to put in it). And then of course about 1GB swap.


Glad to see someone come over from Vista! :)

---

### Post by newlinux on 2007-08-21
Most reports I have seen say ntfs-3G is okay, but that doesn't eliminate the risk of corruption... Just depends on your comfort level. I'd stay away from making anything but a very small partition FAT32. To slow, too many restrictions, too unstable.

---

### Post by ddrichardson on 2007-08-21
I would leave the HP restore partition. Even though it only lets you make one set of recovery disks, it's used for restore (at least on my laptop) from BIOS rather than a bootloader.

Having just installed Ubuntu 7.07 on an HP laptop, I encountered some showstopping problems, but got there in the end. Which model is it.

> FAT32. To slow, too many restrictions, too unstable.

I'm curious as to how you come to this conclusion, accepting that there are the 4Gb file size limitation and the lack of journaling or permissions, FAT32 is stable. In fact it's also a lot more widely supported. I'd be inclined to consider FAT32 support as far more stable than NTFS at present.

---

### Post by mikewhatever on 2007-08-21
FAT32 is the easiest solution if the partition is used for storage. You do not get too many reads to it, so the files do not get fragmented. I have not noticed any slowness restrictions or unstable issues with FAT32.
Both ntfs and ext3 should do just fine too, but will need drivers.

---

### Post by ergo_emm on 2007-08-21
> **ddrichardson said:**
> 
Having just installed Ubuntu 7.07 on an HP laptop, I encountered some showstopping problems, but got there in the end. Which model is it.


It's a Pavilion dv2000, Intel 2 gb dualcore. When running the livecd, the only problem I found was that my wireless card wasn't recognized... anything else I should be aware of?

---

### Post by newlinux on 2007-08-21
> **ddrichardson said:**
> I would leave the HP restore partition. Even though it only lets you make one set of recovery disks, it's used for restore (at least on my laptop) from BIOS rather than a bootloader.

Having just installed Ubuntu 7.07 on an HP laptop, I encountered some showstopping problems, but got there in the end. Which model is it.



I'm curious as to how you come to this conclusion, accepting that there are the 4Gb file size limitation and the lack of journaling or permissions, FAT32 is stable. In fact it's also a lot more widely supported. I'd be inclined to consider FAT32 support as far more stable than NTFS at present.

From my own personal experience with data corruption with FAT32, and testing read/write speeds with FAT32 compared to other filesystems. I was talking about the filesystem itself, not the Linux support for it. I agreethe support for it is more stable than NTFS. I should add the caveat that my testing mostly involved larger files (not larger than 4GB obviously) and larger FAT32 partitions.

If one is okay with using FAT32 as a filesystem at all, then Linux support for it is pretty stable. For me,  the filesystem itself is a no go for anything I'll use frequently with larger files.

---

### Post by ddrichardson on 2007-08-21
If you got the Live CD to boot without any problems then you're fine. I had trouble with APIC that stopped me getting that far.

According to HP's web site - that machine has an Intel Wireless card which is very well supported.

---

### Post by ergo_emm on 2007-08-21
> **ddrichardson said:**
> If you got the Live CD to boot without any problems then you're fine. I had trouble with APIC that stopped me getting that far.

According to HP's web site - that machine has an Intel Wireless card which is very well supported.

That's good to know :) I have a readily available wired connection, so I figured it might be easier to get Ubuntu on the machine first, then figure out the wireless issue.

---

### Post by ddrichardson on 2007-08-21
It may just be a job for ndiswrapper. The laptop I have has a touchscreen which was the biggest headache, not to mention that the display can switch from portrait to landscape.

---

