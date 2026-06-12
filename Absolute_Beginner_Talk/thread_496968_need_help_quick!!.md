---
title: "need help quick!!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-07-09
i'll try to word this as short as i can

- i wanted to resize partitions to give more space to linux (i dualboot) - (ntfs{boot}|ext3{linux}|swap|ntfs{extended})
- i went into windows and decided to use partition magic - dont ask me why i did, i dont know either
- set it to resize, and left
- when i came back, pc was off. i booted, started windows to see if it worked
- i got bsod after boot screen
- i went into linux, manually mounted ntfs partitions, readonly
- booted into gparted live cd, tried to resize
- windows partition is unreadable and it didnt want to resize the other ntfs
- booted into windows xp cd to repair windows
- it didnt see windows, and wanted me to install from scratch
- i quit w/out doing anything and wanted to boot into linux to backup and wipe the windows partition
- no more grub, it loads windows auto which then gets bsodded
- i find [this](http://www.daniweb.com/blogs/entry708.html) guide to fix grub, but it doesnt help because it says that partition is mounted when its not

plz help, i cant use my pc at all :(

---

### Post by HereInOz on 2007-07-09
Frankly I think you are in a spot of bother.   If you have a second HDD I would install ubuntu on that drive then mount the original drive and recover what data is available from the original drive, then re-install.

Sorry for being a prophet of doom, but that is about all I can think of at this point.

---

### Post by supersonicdarky on 2007-07-09
can i install dsl to a usb stick and try to recover with that?

---

### Post by gn2 on 2007-07-09
Have a look in the Hermanzone link in my sig, there might be a solution in there somewhere.
.
One solution would be to put the drive in an external enclosure to transfer files from it to another PC.
.
Partition Magic should NEVER be used to perform operations on Linux partitions.
.
I always use Partition Magic to shrink NTFS, then Gparted to increase ext/3 into the vacated space.
.
When creating a dual-boot I always use PM to reduce the NTFS to create unallocated space then install Linux into that.
.

---

