---
title: "NTFS being stubborn...I hate Windows"
date: 2012-12-29
forum: Any Other OS
---

### Post by gowings83 on 2012-12-29
Here's my story, I had been running Ubuntu 12.10 off a external HDD (laptop had no internal).  Then I got a internal HDD a few days ago since I had to run Windows for school.  So I backed up all my data on my external drive and formatted it to NTFS with gparted.  It shows up as NTFS and empty, even mounts in Ubuntu, but won't in Windows.  It sees the drive, but doesn't mount it, probably cause there's no drive letter right.  I got the free version of partition magic on Windows thinking ok lets do it here and give it a drive letter and it doesn't see the drive.  So what do I do here to be able to use that NTFS drive in Windows now.  All I want it for is basically to put movies, music, pictures, all that stuff since the internal drive is nowhere near big enough.  So versions I'm running is Ubuntu 12.10 alongside XP.  Any help is great guys :)

---

### Post by TheFu on 2012-12-29
WinXP doesn't support GPT partitions (rather than MBR).  Could that be the issue?

I'd use "**Disk Manager**" in WinXP to find the partition and format it as NTFS. Be certain you have the correct HDD selected.  You can also assign a drive letter using that tool.

---

### Post by audiomick on 2012-12-29
That is actually a windows question, but...

XP has it's own partitioning tool, doesn't it? I would try re-formatting the drive with that.

---

### Post by oldos2er on 2012-12-29
Moved to Other OS/Distro Talk.

---

### Post by flavouride on 2012-12-29
Take the offer and upgrade to Windows 8 before 13 Jan 2013.

The support life cycle for XP SP3 is over soon anyway.

---

### Post by gowings83 on 2012-12-30
I got the issue worked out, I just boot n nuked the drive then formatted it in Windows.  Oddly 50GB of the drive is missing.

---

### Post by flavouride on 2012-12-30
> **gowings83 said:**
> I got the issue worked out, I just boot n nuked the drive then formatted it in Windows.  Oddly 50GB of the drive is missing.

I encountered the same every time when I tried shrinking/extending an ext4 partition. Need Gparted check for errors to grow the filesystem size to match the partition size.

But it could be another issue: harddisk manufacturers and linux sees 1GB as 1000MB while Windows sees 1GB as 1024MB. So there oughts to be a mismatch and the capacity looks smaller in Windows.

---

