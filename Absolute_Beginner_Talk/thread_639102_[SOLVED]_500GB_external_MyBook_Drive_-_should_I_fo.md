---
title: "[SOLVED] 500GB external MyBook Drive - should I format it ext3 or NTFS"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-12
whats a better way to go for external drives, ext3 or ntfs

in regards to **Speed**, etc
but then
**Disk Mount Check** is something i would not like to have each time i plug in and mount an ext3 drive

also is it possible to format in ubuntu without unmounting?

---

### Post by Tristicus on 2007-12-12
If you do it in FAT32, it will be recognized more widely.
NTFS is mainly for Windows I THINK.

---

### Post by Pumalite on 2007-12-12
If using Windows, format ntfs. If using Linux, format ext3. You could format ntfs because Ubuntu can read/write to ntfs. Formatting implies partitioning and this is done best with an unmounted driive. ( in fact, is the ONLY way I do it)

---

### Post by MozartlovesUbun2 on 2007-12-12
> **Tristicus said:**
> If you do it in FAT32, it will be recognized more widely.
NTFS is mainly for Windows I THINK.

yes thats how its shipped

but fat32 will not work for over 4GB data

---

### Post by thelatinist on 2007-12-12
If you want to share with Windows use NTFS.  If you want to use it only in Linux, then use ext3 or reiserfs.

---

### Post by aktiwers on 2007-12-12
I used FAT32 on my sisters MyBook 500gb so she could use it on her Mac, my Linux box and my friends Windows box.

Windows dont read/write to ext3 (without plugin installation)
Linux can handlre Ntfs, but does FAT32 better
Dont know about OSX, but I dont think it can handle NTFS.. donno.

FAT32 works on them all.

But if its for Linux only use, I would recommend EXT3

---

### Post by thelatinist on 2007-12-12
> **MozartlovesUbun2 said:**
> but fat32 will not work for over 4GB data

If you're looking for good handling of very large files, I hear that XFS is the best way to go.

---

### Post by MozartlovesUbun2 on 2007-12-12
> **aktiwers said:**
> I used FAT32 on my sisters MyBook 500gb so she could use it on her Mac, my Linux box and my friends Windows box.

Windows dont read/write to ext3 (without plugin installation)
Linux can handlre Ntfs, but does FAT32 better
Dont know about OSX, but I dont think it can handle NTFS.. donno.

FAT32 works on them all.

But if its for Linux only use, I would recommend EXT3

I guess fat32 is out of the question as i cant put anything on it over 4GB big.

**but how good is linux now with NTFS, i mean does it happen that linux corrupts NTFS when reading and specially writing on it?**

---

### Post by MozartlovesUbun2 on 2007-12-12
> **thelatinist said:**
> If you're looking for good handling of very large files, I hear that XFS is the best way to go.

**XFS ** never heard of it

will garted do it for me?

hmm, ok so first i have to unmount the disk, then format it, but if i unmount it will i still be able to see it?

---

### Post by aktiwers on 2007-12-12
Since 1 year ago the ntfs-3g (what makes it possible to read/write to ntfs from linx) announced it was stable. So I dont think you will have any problems with it. Only I have seen is people with mount problems. It can be fixed by manually mounting, but I think those with these problems were running an old install.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

I believe ntfs-3g comes with Ubuntu from Feisty and up. Else automatix2 will install it in no time or a sudo apt-get install :)

---

### Post by jmate24 on 2007-12-12
i have a 120 GB MAXTOR that i can format FAT32. i use the boot CD that came with it.

---

### Post by Stormspireiv on 2007-12-12
Write support for NTFS in linux is slow and resource hungry.  If you want to be writing big files from linux do not go NTFS.

---

### Post by rmockler on 2007-12-12
Just a thought, depending on your situation.  I have a dual boot system, so I formatted my The Book drive for backups with half of it as NTFS and the other half as EXT3.  Fat32 was out because backups for both sides created image files that were greater than 4 GB.  Now I just backup my Windows parttion to the NTFS and my Ubuntu to the EXT3, works like a charm.  I did the repartitioning with gparted, with the drive unmounted.  Gparted saw  it just fine while unmounted, then when finished I rebooted and everything was great.

---

### Post by MozartlovesUbun2 on 2007-12-13
does the ext3 external drive also do disk mount checks?

how about if i need to make some encrypted files?

---

### Post by rmockler on 2007-12-13
Well, I have been backing up to the external drive for three months, and I have not seen a request for a disk check on it yet.  I see no reason why you would have any problems with encrypted files.

---

### Post by Blojic on 2007-12-13
> **MozartlovesUbun2 said:**
> yes thats how its shipped

but fat32 will not work for over 4GB data

Yes it does. The limit is >2TB - the problem with FAT32 is that over 32GB the cluster size jumps to 32KB which makes it inefficient, especially with lots of small files/directories.

If it were me I'd go NTFS for compatibility with Win. should you ever need it.

Ta,

---

### Post by anaconda on 2007-12-13
> **Blojic said:**
> Yes it does. The limit is >2TB - the problem with FAT32 is that over 32GB the cluster size jumps to 32KB which makes it inefficient, especially with lots of small files/directories.

If it were me I'd go NTFS for compatibility with Win. should you ever need it.

Ta,
well.. you CAN make over 4GB partitions as fat32, but you can't have a single file that is bigger than  4GB in a fat32 partition..

I would go the ext3 route.. because it works best in linux and it can be r/w accessed from windows with drivers installed

---

### Post by Blojic on 2007-12-13
> **anaconda said:**
> well.. you CAN make over 4GB partitions as fat32, but you can't have a single file that is bigger than  4GB in a fat32 partition..

I would go the ext3 route.. because it works best in linux and it can be r/w accessed from windows with drivers installed

I wasn't aware of the windows drivers. ext3 it is then...

---

### Post by tgalati4 on 2007-12-13
Put on 4 primary partitions:

1) FAT32
2) NTFS
3) EXT3
4) HFSPlus

That way everybody will be happy.  Also post your performance experience after a year of use.  That would be helpful and it will answer your question.

---

### Post by MozartlovesUbun2 on 2007-12-14
> **tgalati4 said:**
> Put on 4 primary partitions:

1) FAT32
2) NTFS
3) EXT3
4) HFSPlus

That way everybody will be happy.  Also post your performance experience after a year of use.  That would be helpful and it will answer your question.

**I WANT LUDICROUS SPEED, NOW!!!**

*good thing you had that helmet on*

---

### Post by bigken on 2007-12-14
> **tgalati4 said:**
> Put on 4 primary partitions:

1) FAT32
2) NTFS
3) EXT3
4) HFSPlus

That way everybody will be happy.  Also post your performance experience after a year of use.  That would be helpful and it will answer your question.


I think this would be a very good way to see what is the best file system then when you decide which one to stick with you can move your files folder ect to it and use gparted to delete the others and and resize the desired partition :)

---

### Post by rockinlinux on 2007-12-14
i would go ext3, it does not fragment (almost). This is of course if you are using it for linux only....i have neer used the ext3 drivers for windows but hear they wor well. Also you seem to be worried about disk checks....you know you can turn them off or so they only do it ever 100 times or so.... :)

---

