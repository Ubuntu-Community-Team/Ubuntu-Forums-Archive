---
title: "writing to NTFS partitions"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by simonsphotos on 2007-02-17
Well I have set up Ubuntu on my pc and I told it to use (have access to) my windows NTFS partitions so that I can still access my stuff like photos ecc. but I find that I cannot write to these partitions but only read from them, how I can I make it so that I can write to them as well ?

---

### Post by Maestro23 on 2007-02-17
> **simonsphotos said:**
> Well I have set up Ubuntu on my pc and I told it to use (have access to) my windows NTFS partitions so that I can still access my stuff like photos ecc. but I find that I cannot write to these partitions but only read from them, how I can I make it so that I can write to them as well ?

This thread should help: [http://www.ubuntuforums.org/showthread.php?t=363101&highlight=writing+to+ntfs](http://www.ubuntuforums.org/showthread.php?t=363101&highlight=writing+to+ntfs)

---

### Post by jvc26 on 2007-02-17
You will have to install the [ntfs-3g]("http://www.ntfs-3g.org/") drivers. The install instructions for Ubuntu should be on the forums somewhere - apologies, I have lost the link :)
Il

---

### Post by simonsphotos on 2007-02-17
perhaps I should use FAT32 partitions ? I think they are supposed to be more performing anyway aren't they ? I did here that NTFS is not all that it was cracked up to be

---

### Post by Spike-X on 2007-02-17
I've been writing to my NTFS drives since day one using ntfs-3g, and I haven't had a problem yet. I've read that the process isn't perfect yet, though, so **proceed at your own risk!**

---

### Post by Velotix on 2007-02-17
NTFS is more reliable than FAT32 because it's less likely to corrupt of its own accord and destroy your data. My Win98SE computer broke itself down once. However, there is currently no stable driver for read/write access to NTFS in Linux that retains file permissions (hence anyone, anywhere, can go crazy on your NTFS drives and there's nothing you can do to stop it).

That said, FAT32 doesn't even HAVE file permissions, so you're not really losing anything. A driver does exist for read/write NTFS though, hopefully it will be declared stable soon as it's progressed to release candidate stage. That driver is ntfs-3g, which others before me have recommended to you already.

My point? DON'T. USE. FAT32!

---

### Post by simonsphotos on 2007-02-18
yea I just though also I have big drives and I don't think FAT will work with it, I am getting a 320 GB drive in a week ok it will have a couple of partitions but there will still be one huge one

---

