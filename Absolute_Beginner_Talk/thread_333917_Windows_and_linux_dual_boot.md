---
title: "Windows and linux dual boot"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-08
okay i have a big problem. I dual boot vista and feisty fawn. Whenever i re-install grub or linux windows always goes spastic. It says "/windows/system32/winload.exe" is currupt or missing. If i try to repair it doesn't work and if i use the windows cmd on the disk everything is missing. nothing is in the windows folder or the users folder (the equivalent of documents and settings in vista).


This happens everytime]:mad: if i try to mount the windows partition after this happens i get this:

sudo mount hda1
mount: special device /dev/disk/by-uuid/42E48EAFE48EA52F does not exist

Any ideas?

---

### Post by ajmorris on 2007-01-08
also it is not a problem with feisty fawn as this happened before when i had dapper. It never used to happen but then suddenly started just before i re-installed ubuntu with feisty.

---

### Post by spin2cool on 2007-01-08
How are you partitioning your hard drive?  Without that info, I can't help you much.

What I generally do is create four partitions:

1) Windows NTFS
2) Ubuntu / ext3
3) Linux swap
4) FAT32 for data

It's generally easiest to install windows first, because Ubuntu will play nice with pre-existing windows installations (the converse is not true)

---

### Post by ajmorris on 2007-01-08
my windows in ntfs (obviously)

Linux is ReiserFS
Also the linux swap file partition

I have an acronis bootloader on another partition (fat32)

---

### Post by ajmorris on 2007-01-08
and those of you proficient with windows i just remembered that this started happening after i made acronis recognise vista (it doesn't recognise it as a partition yet). What i did was make a boot.ini file by altering the one that windows xp has. Then from my xp cd i added ntdlr and ntdetect.com (all three were added to the root of windows partition (C:\))


could vista have a problem with these files?

---

### Post by spin2cool on 2007-01-08
Yeah, this isn't a linux issue - you hosed your bootloader somehow.  Why not just use GRUB?

---

### Post by ajmorris on 2007-01-08
i was using both. Acronis booted into grub. It was so if i re-install windows then i can still boot linux without re-installing grub.


I didn't hose my bootloader i must have hosed windows.
Thanks anyway.

---

