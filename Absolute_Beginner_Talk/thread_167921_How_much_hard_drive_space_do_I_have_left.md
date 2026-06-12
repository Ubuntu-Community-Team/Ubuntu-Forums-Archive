---
title: "How much hard drive space do I have left?"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by MarkTBSc on 2006-04-29
I've installed Ubuntu on an old 40Gb HDD I had laying around. When I go into Administration/Disks Manager it correctly detects it as 37.31Gb and shows that /dev/hda1 is Extended 3 with the access path /boot.

In size it says that I have 243MiB with 193 remaining (this is partition 1) but if I go over to Partition 5 then it says the file system is unformatted and that while the free space is 37Gb, the free space is not available. It also states that its status is inaccessible.

This is strange because I've got at least 3.6Gb in my home directory and, apparently, 22Gb of free space left.

What am I missing? Is there something I need to do to get my drive space reported correctly?

---

### Post by user1397 on 2006-04-29
I would pay more attention to what your home folder says than the disk manager.
what it says truly doesn't make sense...

---

### Post by MarkTBSc on 2006-04-29
[QUOTE=erik1397]I would pay more attention to what your home folder says than the disk manager.
what it says truly doesn't make sense...[/QUOTE]

True, but surely there has to be a better way to keep track of my disk space than by going around, making sure you can view all the files and then totting up how much they use and subtracting that from what you think you've got on the drive?

One of the nice things about Windows is that you can go into My Computer, click a drive and it'll give you a nice pie-chart of the drive usage.

Is there no way for Linux to do that?

---

### Post by Rinzwind on 2006-04-29
In general I use
df -h


Disk admin sucks :)

---

### Post by MarkTBSc on 2006-04-29
[QUOTE=Rinzwind]In general I use
df -h
[/QUOTE]

Aha! Now that's useful, thanks!

---

### Post by The Mekon on 2006-04-29
There is a nice utility under Applications>SystemTools>System Monitor>Devices which provides all disk usage details.

---

