---
title: "Partition questions"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by vx1 on 2007-07-25
Hey everyone,
I'm installing Ubuntu for the first time. I want to dual-boot with Vista (not quite comfortable enough with Linux yet).  

So I was following the Vista dual-boot instructions ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)) and I got to the resizing part, where it says: Choose the First Option (It should be something like: "Resize IDE1 master, partition #1 (hda1) and use freed space").

I don't have that option...  I have
Guided - Use entire disk
Manual

Anyway, I'm willing to do it manually, I just have a few questions...

Does the type matter?  Can I just use ntfs?
The computer's a Dell, I got it with two drives in a RAID1 configuration.  Do I need to do anything special when I'm resizing?
Also, I've heard mention of problems with partitioning during the install, and Vista not being able to boot afterwards.  Should I be worried?  Or is there another way to do it?

Thanks very much!

---

### Post by por100pre1 on 2007-07-25
Did you shrink Vista's partition first? You can do it using Vista's Disk Manager. You may need to use Disk Defragmenter first.

EDIT: Type matters. Ubuntu uses ext3 file system.

---

### Post by az on 2007-07-25
> **vx1 said:**
> 
Does the type matter?  Can I just use ntfs?

Even if you could use ntfs, you would still have to create a separate partition.


> **vx1 said:**
> 
The computer's a Dell, I got it with two drives in a RAID1 configuration.  Do I need to do anything special when I'm resizing?

You shouldn't.

> **vx1 said:**
> 
Also, I've heard mention of problems with partitioning during the install, and Vista not being able to boot afterwards.  Should I be worried?  Or is there another way to do it?


The problems with partitioning newer (Vista) ntfs partitions were corrected in the version of libntfs in Ubuntu before Feisty was released.

---

### Post by vx1 on 2007-07-27
Ok, so I tried to partition the first drive...

I resized one of the existing partitions that had about 187000MB to 147000MB.  Now I have a partition that is about 40000MB and is labeled "unusable."  
I can't undo it or format it.  When I try to move forward, it says "No root file system is defined."  

I went back, and the option "Guided - use the largest continuous free space" is available.  When I pick that I get "Partitioning failed because the chosen free space may not be used.  There are probably too many (primary) partitions in the partition table.

By the way, do I have to partition my second drive in the same way?  I can't right now, when I try to resize it and click Ok it doesn't do anything (the dialog just closes, no messages or anything, and no resizing).

I have no idea what to do.

---

### Post by vx1 on 2007-07-27
Could someone walk me through this or something?
I've been trying to figure it out myself, and I think I just deleted about 20 gigs of files from somewhere.  I don't know where, I just know that I now have 20GB more space free on C: than I had a few minutes ago.  So yeah, that's pretty much all I've been able to accomplish, and I'm just gonna stop there.
I'd really appreciate it if someone could give me a clue here...

Edit: Also, should I be worried about that 20GB?  Nothing seems to be missing right now; Windows boots, my files and programs still seem to be around...  I'm just wondering if this'll come back to haunt me somewhere down the line.  I feel like 20 gigs of something should not be working anymore...

---

### Post by vx1 on 2007-08-03
Anyone?  I still haven't been able to get anywhere.
I also tried freeing up the space using the Windows disk manager first, but I still get the same errors.
I don't really know what else to try.

---

### Post by az on 2007-08-03
You need to delete that new partition.  That will create the free space.  Free space in this context is unpartitioned space.

The Ubuntu installer should then be able to use it.

---

### Post by Inxsible on 2007-08-03
Also keep in mind that you can have at most 4 primary partitions. so create an extended partition and then create additional partitions within it.

---

### Post by az on 2007-08-03
> **Inxsible said:**
> Also keep in mind that you can have at most 4 primary partitions. so create an extended partition and then create additional partitions within it.

The installer would take care of that for you when you use guided partitioning.

---

### Post by vx1 on 2007-08-05
Ok, thanks very much guys.  I think it was the number of partitions.  I deleted an existing partition and just left the space unallocated, and then the installer let me use Guided with the largest continuous space.  So I think I've got it installed now.

New problem, though: how do I start it?
I don't get an option to choose the OS when I start my computer.  Windows Boot Manager only lists Windows Vista.  The Boot Device Menu lets me choose 

Intel ARRAY, which just seems to start Windows, 
Onboard or USB CD-ROM Drive,

System Setup,
Hard Drive Diagnotics,
Boot to Utility Partition

If I pick Boot to Utility Partition, "GRUB" is printed below the list, but then it just stops.  It doesn't seem to be an option or anything, pressing keys doesn't do anything.

So now what?

---

### Post by vx1 on 2007-08-10
Sorry to be a pain,  but I'm still lost.

I've been doing some searching, and I figured that since I don't get the option to choose which OS to use, maybe I needed to reinstall/restore grub.  So I followed the instructions for that, and still no luck.

Then I tried editing menu.lst.  I followed the instructions, but when I tried gksudo gedit /boot/grub/menu.lst, I just got a blank file.

So I'm back to being out of ideas, still open to suggestions, if anyone has them.

Thanks.

---

### Post by Paul133 on 2007-08-10
Wait? You're in Ubuntu now or Windows?

---

### Post by vx1 on 2007-08-10
Sorry...  I  had Vista installed already, and can still boot into that.
I installed Ubuntu, but I never get the option to boot into it.  I've been using the live cd when I need it.

---

### Post by Paul133 on 2007-08-10
So whenever you turn on the computer and boot from the HD, Vista just starts?

---

### Post by vx1 on 2007-08-10
Yes.
The closest I got to anything else was what I mentioned in an earlier post, hitting F12 before Windows starts to load and getting a menu where I can choose to boot from a utility partition, and it prints out "GRUB," but nothing ever happens, no keys work, and eventually I just have to ctrl+alt+del.

---

### Post by Paul133 on 2007-08-10
Sounds like there's a problem with GRUB, though I can't tell what it is. Maybe you should try Super GRUB: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by vx1 on 2007-08-10
Ok, I'll give that a shot.
Thanks very much.

---

### Post by Paul133 on 2007-08-10
Good luck. Let me know how it works out.

---

