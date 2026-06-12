---
title: "HOWTO: Read/Write USB external NTFS HDD"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by oakey_99 on 2006-07-12
Hey all,

Just bought a 320gb Seagate HDD and have it in an external case connected via USB.
It mounts automatically but i cannot write to it, simply states permission is denied.

I know that writing to NTFS isnt the best idea from unix ... 
Issue is that i use both windows and unix and have teh external to hold music, vids etc etc and would like both operating systems to be able to read it and write it.

What are your best suggestions ?

---

### Post by Kilz on 2006-07-12
> **oakey_99 said:**
> Hey all,

Just bought a 320gb Seagate HDD and have it in an external case connected via USB.
It mounts automatically but i cannot write to it, simply states permission is denied.

I know that writing to NTFS isnt the best idea from unix ... 
Issue is that i use both windows and unix and have teh external to hold music, vids etc etc and would like both operating systems to be able to read it and write it.

What are your best suggestions ?

Convert it to fat32, both OS's can read and write to it then. There are **experimental** ways of writing to a ntfs partition. Experimental like "I just made brake pads out of Swiss cheese for my car, lets all go for a ride". You take a big chance of corrupting the entire disk and losing everything on it.

---

### Post by MrHorus on 2006-07-12
> **Kilz said:**
> Experimental like "I just made brake pads out of Swiss cheese for my car, lets all go for a ride". You take a big chance of corrupting the entire disk and losing everything on it.

NTFS Write Support has been "experimental" for years and i've used it for many of those years and never lost a single bit of data yet.

Of course, just because I have been problem free doesn't mean that *YOU* will be.

YMMV.

---

### Post by xrchris on 2006-07-12
You could always use EXT3 and install [Ext2 Installable File System for Windows]("http://www.fs-driver.org/") instead.

---

### Post by huangjiahua on 2006-10-10
I think you can use ntfs-3g,
[http://ubuntuforums.org/showthread.php?p=1601663](http://ubuntuforums.org/showthread.php?p=1601663)

---

### Post by stalker145 on 2006-10-10
> **Kilz said:**
> Convert it to fat32, both OS's can read and write to it then. There are **experimental** ways of writing to a ntfs partition. 

Be wary of converting the **entire** drive to FAT32.
["FAT32 partition sizes are limited to 32GB in size using the native FAT32 file system format tools under Windows 2000 and Windows XP. (The maximum size is 127.5 GB practical and 2TB standard theoretical.)"]("http://www.mcmcse.com/windows_xp/guides/filesystems.shtml")
I have several drives that are well over the "practical" size for FAT32, but I don't plan on ever going back to MS. IANAMSCE (I am not an MSCE), so please don't take my word on it, but I think it would be best split your drive into at least two partitions to bring it to within the 127GB as mentioned.
If I'm wrong, let me know... I've been known to be wrong many times in my life ;)

---

