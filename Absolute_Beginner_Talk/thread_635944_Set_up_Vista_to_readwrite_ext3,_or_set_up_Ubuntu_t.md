---
title: "Set up Vista to read/write ext3, or set up Ubuntu to read/write ntfs?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-09
A thread of mine recently got to the point where it made me want to start a new thread...
I posted about dual booting ubuntu with vista but I now have a broader question.

One member mentioned that while 7.10 read/writes ntfs, he has occasionally lost some files to corruption in the process (especially with image files, I assume he means photos) while trying to share an ntfs partition with vista. Ubuntu will read the file, close it, and then upon opening that files in vista it is corrupted.

Now for my question: I was thinking of making three partitions on my 120gb hdd - one for vista, one for linux, and a shared ntfs partition. Has anyone experienced these types of corruption problems in using a shared ntfs partition, or in using a shared ext3 partition? In other words, would it be more reliable to have vista write to ext3 or for ubuntu to write to ntfs? Ultimately I may split things up 50/50 on the same hard drive, but it wasn't quite what I had in mind.

This is great forum - thanks for helping the nOOb.

---

### Post by Joeb454 on 2007-12-09
Go for FAT :p

---

### Post by spydon on 2007-12-09
> **TheNorthWaves said:**
> A thread of mine recently got to the point where it made me want to start a new thread...
I posted about dual booting ubuntu with vista but I now have a broader question.

One member mentioned that while 7.10 read/writes ntfs, he has occasionally lost some files to corruption in the process (especially with image files, I assume he means photos) while trying to share an ntfs partition with vista. Ubuntu will read the file, close it, and then upon opening that files in vista it is corrupted.

Now for my question: I was thinking of making three partitions on my 120gb hdd - one for vista, one for linux, and a shared ntfs partition. Has anyone experienced these types of corruption problems in using a shared ntfs partition, or in using a shared ext3 partition? In other words, would it be more reliable to have vista write to ext3 or for ubuntu to write to ntfs? Ultimately I may split things up 50/50 on the same hard drive, but it wasn't quite what I had in mind.

This is great forum - thanks for helping the nOOb.

I have never got anything corrupted on my NTFS partion, ntfs-3g work very well.

---

### Post by FSHero on 2007-12-09
Hello there,

I'm a bit of a newbie myself, but I think I have a solution:
Use a FAT32 partition.

This way, you don't have to install any extra utilities in either operating system (to let Windows access ext3, you would need an additional program -- don't know what, though).

Both are guaranteed to work with FAT32, too.

Finally, I highly recommend you set up one /home partition, so *in case* you want to replace Ubuntu with another GNU/Linux distro, or you want to "experiment" with stuff, the files on your /home partition will be preserved. I would probably assign 1GB for that, just for "backup purposes".

---

### Post by SOULRiDER on 2007-12-09
Ive used ntfs rather heavily and never lost a file or got one corrupted. If youre not going to store files larger than 4 GB then go for FAT32. If you know youre gonna need either ext3 or NTFS, I suggest you go for NTFs and let windows use that partition natively. Theres a simple reason for this actually.

If you install ext drivers on windows it will be able to write files to your linux partition, meaning that if you happen to get a virus or something you will be putting your linux installation at risc (not of getting a virus on linux since it wont work, but of losing important data). If you use ntfs in linux you can select which partitions to actually mount so theres not even a reason to mount your windows partition and you wont be risking anything.

---

### Post by TheNorthWaves on 2007-12-09
so the only downside i see to this would be... the necessity to reinstall the windows software in order to format the entire hdd in fat32 - correct? I wanted to avoid that, but it's more important to me that I have a solid installation/dual-boot setup with minimal problems and full sharing of files between platforms.

And a Q for the last poster - is there a reason I would need to run an ext3 partition? (ie: to run compiz/xgl?)

A friend just told me a moment ago that FAT32 isn't a formatting option, it requires ntfs in the vista installer....

---

### Post by SOULRiDER on 2007-12-09
If you already have the partition made theres no need to reinstall windows or anything, just format the partition as FAT32. If the partition si not made youw ill ahve to resize the existing partitions and thenf romat the resulting space. 

A filesystem is independent from what you can install on it.EXT3 is justa  filesystem, its a way to store files, you can put the same things you can put on a FAT ot NTFS partition, and no, you still will not have to reinstall anything BUT you WILL have to install drivers in windows to use an EXT3 partition sicne windows doesnt support them.

---

### Post by TheNorthWaves on 2007-12-09
ah ok - keep the vista partition in ntfs, install 7.10 on an ext3 partition, and have the shared files on a fat32 partition (or ext3 and use windows driver) - got it. Thanks.

---

### Post by SOULRiDER on 2007-12-09
I actually meant, the new partition should be FAT or NTFS, i wouldnt recomment making Ext3, but thats your call.

---

