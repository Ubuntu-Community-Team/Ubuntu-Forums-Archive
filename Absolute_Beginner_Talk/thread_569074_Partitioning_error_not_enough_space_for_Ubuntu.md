---
title: "Partitioning error: not enough space for Ubuntu"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Iendicis on 2007-10-06
I finally got the guts to start up the installer on Ubuntu (Feisty Fawn) and I soon discovered that my hard drive was consisted of two chunks: the 74 GB of Windows data (50 GB in use, 24 GB free) and about 2 GB of free space, which Ubuntu offered to cram itself into. I didn't want that headache so I went on a mission to find a suitable partition editor to grab a few more GB for Ubuntu to share (I plan on 10), and soon discovered another headache: my hard drive had a "bad sector" that made my disk so that Gnome partitioner wouldn't make anything smaller.

I used the Gnome Partitioner in Ubuntu as well as the standalone LiveCD to check this, and the LiveCD told me, basically that, "The disc has a bad sector, which might be from a physical issue. Scan the disk for errors." So using Windows' Scan Disk, I did, and that didn't help (even after a good half and hour of scanning). I've been using this hard drive for a year, and I know it's been around for about three or four in a university (it has a "made for Windows 2000" sticker").

I know that if there a physical deformation on the disc, I will probably have to replace it, but is there possibly another way of helping this HD before it goes down the tube? Also, is there a way I can make a place for Ubuntu if there isn't an issue (I might just use Xubuntu, but I still won't have a whole lot of room in 2 GB...)

---

### Post by nickburns on 2007-10-06
I vote that you spend $100 bucks and get a new HDD.

---

### Post by Iendicis on 2007-10-06
> **nickburns said:**
> I vote that you spend $100 bucks and get a new HDD.

Already on the list; my dad has ten or fifteen smaller HDs that I plan on stealing for all of my evil OS plans.
I'm really only looking for a temporary solution.

---

### Post by irish_flu on 2007-10-06
If the disk does indeed have a physically bad spot, I recommend keeping your partitions as they are; resizing might not be a very happy experience.

---

### Post by Iendicis on 2007-10-06
> **irish_flu said:**
> If the disk does indeed have a physically bad spot, I recommend keeping your partitions as they are; resizing might not be a very happy experience.

Should I crack open the comp and look, or is there a way of finding out exactly what's wrong otherwise?

---

### Post by mivo on 2007-10-06
If it is a bad sector, and it sounds like it might be one (did you try defragging the drive in Windows?), you can't really fix that by opening the computer. Personally, I would just throw Windows off the disk and use the 70 GB for Ubuntu, but that is me and I understand it may not be an option. ;) If you can get another drive from your father, I think just snatching one and adding it to the box is probably the best approach. Fastest, too.

---

### Post by irish_flu on 2007-10-07
> **Iendicis said:**
> Should I crack open the comp and look, or is there a way of finding out exactly what's wrong otherwise?

As the poster above me says, there's no way to see whether or not your disk is failing.  Your options are either to trash that disk and start fresh, or keep using it (but keep a backup) knowing that it might go south one day.

If I were gonna try to change the disk partitions on it, I'd just wipe it and make new partitions (insted of resizing what's already there).  The caveat is that when you hit the bad spot, you still may not be able to partition or format that space.

Either way, keep a good backup schedule.

---

