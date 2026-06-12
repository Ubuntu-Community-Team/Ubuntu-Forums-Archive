---
title: "Danger in mounting ntfs rw?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-05
The installer appears to mount all existing ntfs partitions read-write. Is there any danger in this?

I ask cos I appear to have lost 2 harddrives at the same time. (Okay the one was almost 10 years old but the other is less than a year )

BTW. I'm talking about the Feisty Installer

---

### Post by nemilar on 2008-02-05
Ubuntu uses the NTFS-3G driver, which is a mature and stable driver for reading/writing NTFS partitions.  The kernel partition has been (and as far as I know, still is) listed as "Experimental" for writing (not reading) NTFS partitions.

It should be safe to r/w NTFS in Ubuntu using the NTFS-3G drivers.

---

### Post by jw5801 on 2008-02-05
The driver itself wouldn't affect your harddrive itself. A dodgy driver might corrupt the filesystem, but it shouldn't be able to kill the hard-drive itself. Dodgy kernel hardware interfacing is the only thing that could do that from a software standpoint, and the Linux kernel has very little chance of that! It's more likely the second hard drive suffered an impact or something similar. The first one was just old! :p

---

### Post by hyper_ch on 2008-02-05
> **nemilar said:**
> Ubuntu uses the NTFS-3G driver, which is a mature and stable driver for reading/writing NTFS partitions.
Even if it's mature there still might be bugs in it... in that case you might lose all your ntfs data...

---

### Post by Liet_Kynes on 2008-02-05
I'm running another copy of Ubuntu Feisty. I know it originally mounted my ntfs partition rw. How do i check if it has the ntfs-3g installed?

---

### Post by Liet_Kynes on 2008-02-05
> **jw5801 said:**
> The driver itself wouldn't affect your harddrive itself. A dodgy driver might corrupt the filesystem, but it shouldn't be able to kill the hard-drive itself.

Sorry I meant that the files system was corrupted not the harddrive was damaged :) [my 6g Fujitsu still going strong :D ]

---

### Post by hyperair on 2008-02-05
Use Ubuntu Gutsy. It's got ntfs-3g installed by default. Feisty doesn't, so you'll have to install ntfs-3g and ntfs-config as well as run ntfs-config before it'll work.

---

