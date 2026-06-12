---
title: "Accessing Linux Partitions on XP"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-02-10
Hello People,
I have a dual boot system with Win XP (NTFS) and Ubuntu Breezy. I need to take some stuff from Ubuntu to XP because the screen res in Ubuntu is crazy and I cant read it off the pc. (I have tried SO MANY METHODS to set it right....check out my other threads and you will know) I need to access these files directly instead of burning them on a CD and transfering them. 
Any suggestions on how to do this?
Thanks,
Linuxnovice.

---

### Post by TrendyDark on 2006-02-10
If your linux partition is a Ext2/3 you can use this driver in windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by linuxnovice on 2006-02-10
Hello TrendyDark,
Thankyou for your help, it worked beautifully.
Linuxnovice.

---

### Post by TrendyDark on 2006-02-10
No problem, I used the same driver when I had XP installed. You should switch completely, in my opinion ;) lol

---

### Post by lyly on 2006-02-10
[QUOTE=TrendyDark]If your linux partition is a Ext2/3 you can use this driver in windows:
[/QUOTE]

Hum, and if I have a reiserfs linux partition?

---

### Post by TrendyDark on 2006-02-10
Well, thank you for asking that question, I've never looked for one before and I think I told someone a few days ago it didn't exisit. But here's the driver for ReiserFS access under windows:

[http://rfsd.sourceforge.net/](http://rfsd.sourceforge.net/)

---

### Post by Jucato on 2006-02-10
How safe is it to write from XP to ext2/3? I know that it isn't recommended to write from Linux to NTFS. So how about the other way around, since the app you mentioned allows writing to ext2/3?

---

### Post by TrendyDark on 2006-02-10
I've gotten a drive error once, but that was about it. It should be pretty safe, but I would still suggest just making a small FAT32 partition for moving files back and forth, it makes life much easier. And if you do make the partition, make it from the Windows drive, for some reason FAT32 partitions made in Gparted aren't picked up under XP.

---

### Post by tokyovigilante on 2006-02-10
The reason NTFS writes under linux are often referred to as unsafe is that NTFS is a proprietary Microsoft filesystem, and as such the Open Source community can only rely on reverse-engineering the drivers to be able to access NTFS volumes.

Read access is generally not too much of a concern because there is no modification to the filesystem being read, and therefore minimal chance of harm to your data.

However trying to implement write access using a reverse-engineered driver on a proprietary system which Microsoft can modify (read make incompatible with current drivers) at any time is a recipe for disaster, and so is not generally enabled by default. Not to belittle the NTFS guys, they did a great job, and being able to mount NFTS readonly is fantastic for pulling stuff from XP.

On the other hand ext2/3 (ext3 is ext2 with journalling) is an open standard with fully open source, and so the fs-driver.org team know exactly what they're doing when they write the Windows driver for ext2/3. This means write access is generally safe and error-free. I've read and written substantial (GB) amounts of data without issues using the driver.

The caveat with the ext driver is that there is no way for it to respect linux permissions on XP. This means you can mount your root volume and muck about with all sorts of essential system files, without a root password. This is particularly relevant if you don't have a separate /home partition to mount.

However as long as you're careful not to touch anything linux wouldn't let you, you should be fine with any of the open-source filesystem drivers under XP.

---

### Post by danhm on 2006-02-10
[QUOTE=lyly]Hum, and if I have a reiserfs linux partition?[/QUOTE]


I like [YAReG](http://yareg.akucom.de/) for that.

---

### Post by plors on 2006-02-10
[QUOTE=TrendyDark]
<snip> for some reason FAT32 partitions made in Gparted aren't picked up under XP.[/QUOTE]

this is fixed in >=gparted-0.1

---

