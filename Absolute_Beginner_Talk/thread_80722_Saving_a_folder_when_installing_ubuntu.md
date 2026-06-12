---
title: "Saving a folder when installing ubuntu?"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by weneedjuice on 2005-10-22
hello
i had posted a day or so ago about my problems accessing my windows XP partitioning, and now i can access it, but I can't change the permissions (even as sudo/root) because it's a read-only disk. and i can't move it onto another partition because there isn't enough space. 
so basically, i was wondering if there's some way, if i re-install ubuntu, to save the folder with all my downloaded stuff in it and just reformat everything else to be ubuntu. if i can't, do you have any other suggestions?

---

### Post by kanem on 2005-10-23
[QUOTE=weneedjuice]hello
i had posted a day or so ago about my problems accessing my windows XP partitioning, and now i can access it, but I can't change the permissions (even as sudo/root) because it's a read-only disk. and i can't move it onto another partition because there isn't enough space. 
so basically, i was wondering if there's some way, if i re-install ubuntu, to save the folder with all my downloaded stuff in it and just reformat everything else to be ubuntu. if i can't, do you have any other suggestions?[/QUOTE]
If you just want to have read/write access to your download folder I wouldn't reinstall. Even if you did reinstall you wouldn't be able to format the partition with your download folder as a Linux partition without losing the data.
But you should be able to change permissions. The only restriction shoud be if it is an NTFS partition in which case you don't have write permission. The line for my Windows partition in my /etc/fstab file looks like this:

/dev/hda1       /mnt/windows    vfat    uid=you,noatime           0       0

with the 'you' in uid=you replaced with your user name. But this is for a fat32 partition. If you have an NTFS partition it's probably different.

---

### Post by weneedjuice on 2005-10-23
yeah, it's  NTFS unfortunately :???: 

as of yet, i haven't heard of a way to fix this. i'm wondering if i should just burn it all on dvd or move it to an external harddrive and then just reformat the whole thing and move it all back after.

---

### Post by Herman on 2005-10-23
weneedjuice, I think you should try making a small FAT32 partition that both Windows XP and Ubuntu can both read and write to. It only needs to be small, 1GB is all some people need, or even less. There's an example of how I made a 5GB one, and also how to mount your NTFS as read only, and more in my signature link (below). 
It's way down the bottom of the page, in 'part two', so you'll have to scroll down a very long way to get to it. (Sorry about that!) As you will see, you will need to be a little bit brave, because you will recieve a few red warning screens at the end, but it will be worth it when you are finished.        :p

---

