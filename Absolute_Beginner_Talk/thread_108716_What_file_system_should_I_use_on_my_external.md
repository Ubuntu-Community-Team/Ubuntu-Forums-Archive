---
title: "What file system should I use on my external?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Deaf_Head on 2005-12-26
I want both my windows and linux partitions to be able to read adn write to it, but I wasn't sure what would be the 'best' ... so I was hoping I could get some of your guys' thoughts on it.

Ubuntu gives me the options of:
 ext2 
 ext3
 reiserfs
 xfs
 jfs
 windows virtual fat ( Is this fat 32? I googled it and I got people saying "it is but it isn't" citing somethign that seemed trivial)

---

### Post by ninotob on 2005-12-26
If I wanted to this without headaches, I'd format as vfat from windows.  Ubuntu will be able to read and write to that, as will windows as it made the partition.  I'm not familiar w/ windows anymore and it seems I may have heard that there is a way to get ext3 to work on it, but I'll leave that googling to you.  It could well be false memory on part as well, so take that w/ a grain of salt.

---

### Post by jimrz on 2005-12-26
not sure what the diff is between vfat and FAT32. What file system does it currently have?. FAT32 would be best for dealing with both os's. If not currently FAT32, maybe would be best to format it to that on the win side. Take away any doubt about what you actually have.

---

### Post by Deaf_Head on 2005-12-26
It was NTFS .. and windows won't allow me to partition it as anything other than NTFS ... I don't know why .. maybe it was part of a critical security update ... rofl.

I went with vfat .. basically I found an explaination that vfat = fat32, and that vfat was it's real name or something like that. It was difficult to follow .. heh

---

### Post by MetalMusicAddict on 2005-12-26
I would reccommend Ext3. Look at [THIS]("http://www.ubuntuforums.org/showthread.php?t=107311") thread for info. COMPLETELY read through the site it mentions. I use the driver on a USB2 drive.

---

### Post by akniss on 2005-12-26
[QUOTE=Deaf_Head]It was NTFS .. and windows won't allow me to partition it as anything other than NTFS ... I don't know why .. maybe it was part of a critical security update ... rofl.

I went with vfat .. basically I found an explaination that vfat = fat32, and that vfat was it's real name or something like that. It was difficult to follow .. heh[/QUOTE]

Windows won't let you have a FAT32 partition larger than 32 GB, as it becomes extrememly inefficient at writing and relocating on larger drives.  If you wanted to do it from the Windows side, it would be best to make several 32GB Partitions in FAT32.

---

### Post by Landice on 2005-12-26
[QUOTE=akniss]Windows won't let you have a FAT32 partition larger than 32 GB, as it becomes extrememly inefficient at writing and relocating on larger drives.  If you wanted to do it from the Windows side, it would be best to make several 32GB Partitions in FAT32.[/QUOTE]

Yea, that's right. But i think with some 3rd party software, we can create a large drive for FAT32. I just created 1 100GB FAT32 partition as a storage drive for both Windows and Linux... (but i forgot i created it with Partition Magic or Windows Disk Management.. :rolleyes: )

---

### Post by MetalMusicAddict on 2005-12-26
The other thing about FAT32 is the 4gig filesize limit.

---

