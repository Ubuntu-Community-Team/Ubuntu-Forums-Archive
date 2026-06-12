---
title: "are my partitions right?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Heretic on 2006-06-19
I tried to get ubuntu 6.06 to resize my windows partition, but it sucked. So im manually creating partitions and i will assign them during the install.

What would you suggest I change? If anything?

[img]http://img66.imageshack.us/img66/337/partition2jj.jpg[/img]

---

### Post by nalmeth on 2006-06-19
Is your NTFS really toasted?

I don't think Windows will be content being at the end of the drive, but I could be wrong on this one.

EXT3 is the filesystem you want to for Ubuntu, but you can just format that EXT2 when you install anyway. 

If anything, your setup looks kind of, backwards.

---

### Post by Heretic on 2006-06-19
[QUOTE=nalmeth]Is your NTFS really toasted?

I don't think Windows will be content being at the end of the drive, but I could be wrong on this one.

EXT3 is the filesystem you want to for Ubuntu, but you can just format that EXT2 when you install anyway. 

If anything, your setup looks kind of, backwards.[/QUOTE]
I cant really complain, since thats how PartitionMagic automatically set it up. Basically, the Windows part is really just a backup of windows files. I want to be able to install ubuntu on it, so when I boot up it will ask me if i want to boot windows on my primary drive, or ubuntu off of my usb hard drive [toasted].

My pc already has a boot menu that asks, since it used to boot from 2 OSs.

---

### Post by nalmeth on 2006-06-19
Installing ubuntu will overwrite your previous boot-loader, but likely it will still ask if you want to add windows to grub. If its just a data partition with extra "junk" ;) it should be fine.

---

### Post by Heretic on 2006-06-19
Yah Toasted has a small section I want to backup documents, not windows system files. Would I install GRUB on the same HD as ubuntu [Toasted] or on my primary drive [Windows]? Is there a tutorial or paper I can read up on where someone has previously done this?

---

### Post by ProjectGod on 2006-06-19
i'd use ext3 with the journaling system rather than ext2. 

toasted. haha! nice.

my ntfs is dubbed "crispy"

---

