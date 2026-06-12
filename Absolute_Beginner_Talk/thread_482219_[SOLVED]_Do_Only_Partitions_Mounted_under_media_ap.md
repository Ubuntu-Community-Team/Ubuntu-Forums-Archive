---
title: "[SOLVED] Do Only Partitions Mounted under /media appear on the desktop with drive ico"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-23
I mounted two of my internal drive partitions under /mnt and the drive icons do not appear on the desktop. But my external drive which is mounted under /media appears.

Is this how its supposed to be? Is there any way I can have the drive icons for the partitions that I have mounted under /mnt ?

---

### Post by mcduck on 2007-06-23
> **Inxsible said:**
> I mounted two of my internal drive partitions under /mnt and the drive icons do not appear on the desktop. But my external drive which is mounted under /media appears.

Is this how its supposed to be? Is there any way I can have the drive icons for the partitions that I have mounted under /mnt ?
Yes, that's right. Only drives mounted in /media get icons. So just create directories for your drives in /media and then change your fstab to mount those drives there.

---

### Post by Inxsible on 2007-06-23
> **mcduck said:**
> Yes, that's right. Only drives mounted in /media get icons. So just create directories for your drives in /media and then change your fstab to mount those drives there.

Thanks, but i think its cleaner to have my internal drives under /mnt and externals under /media. I have a bunch of them :rolleyes:

I have created launchers on the desktop with the commands like 'nautilus /mnt/Windows' etc. So I can still access them via a double click :)

---

