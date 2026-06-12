---
title: "What will happen to my current drives?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Ali. on 2007-06-19
Well, I have experience in reformating my computer and reinstalling Windows but the whole Linux thing is new to me. I have used a partition manager to divide my harddisk into four drives, of which one has a Windows installation on it (the C drive). The three others have specific content, which are very, very important to me (school work etc.) and I wouldn't fancy it being deleted or messed with.

1) What will happen to my drives if I install Ubuntu? Deletion or something of that ilk?
2) All my school work is basically in Excel and Word formats. Will I be able to read it? And in general, can I use those two programs (through Wine, I assume)?

---

### Post by dreadlord_chris on 2007-06-19
> **Ali. said:**
> Well, I have experience in reformating my computer and reinstalling Windows but the whole Linux thing is new to me. I have used a partition manager to divide my harddisk into four drives, of which one has a Windows installation on it (the C drive). The three others have specific content, which are very, very important to me (school work etc.) and I wouldn't fancy it being deleted or messed with.

1) What will happen to my drives if I install Ubuntu? Deletion or something of that ilk?
2) All my school work is basically in Excel and Word formats. Will I be able to read it? And in general, can I use those two programs (through Wine, I assume)?

Unless you have free space on the drive for Ubuntu to have its own partition(s) - you're gonna need another drive

You should have no problems with Word or Excel formats - there are native solutions (OO) or you can run them thru wine

---

### Post by st33med on 2007-06-19
Also, there is no such thing as a C or D drive in Linux. They are called partitions.

---

### Post by Josey on 2007-06-19
Just make sure to backup important documents externally before making new partitions or resizing or anything.
Be prepared to lose it if you start making new partitions or resizing basically.

You will need at least 2 new partitions for ubuntu.

Excel and Word documents will open in Open Office "out of the box"

---

### Post by Ali. on 2007-06-20
But if I overwrite my current Windows installation with an Ubuntu installation everything will run smoothly? My other partitions will be operating fine (I can access them and use them in general), the Ubuntu system will run fine and I won't have to create new partitions?

---

### Post by Obeleh on 2007-06-20
if you "overwrite" your Windows you will delete EVERYTHING that is still on your C drive
Basicly what you do is:  Delete the windows partition. And install Linux instead.
Note that Linux uses a different File System. Ubuntu runs on Ext3 by default. When you have finished installing you will still be able to read from your other drives (eg. Drive D) but in Linux they will be called Hda2, or Hdb1 depending wheter theyre just partitions or phiscal drives. You will be able to open all Office documents with Open Office like Dreadlord and Josey say.
But because these files are on a different File System (NTFS / Fat32) you cant write there. The easiest thing to do is get automatix. Its a program that has a lot of usefull stuff for ya (read more @ [www.getautomatix.com](www.getautomatix.com) )

But I suggest you either get an extra hard drive or empty up a partition so you can first try a Dual Boot system so that you still have windows to fall back on if you're stuck with something

---

### Post by molly_001 on 2007-06-20
ya Ali [B]sadiq --

Make a 100% backup[/B] of your important data partitions before you install, or try to install anything, and before deleting anything.  If you have a fast internet connection, you can even backup online free of charge at Mozy.com .

After you have done this, you can feel free to continue pursuit of installing Linux.  I have installed Ubuntu on 25 machines and it has never negatively any other partition.

Your habeeb is GParted LiveCD -- get it now to examine partitions on your hard disk and have a good understanding of your plan.

---

### Post by dptxp on 2007-06-20
Do not delete Windows now till you get used to Ubuntu. Free a partition (drive) and not C, run live CD, delete the partition, resize to 6 to 8 GB for / (root) ext3 format as logical drive, resize leaving 1-2 GB for SWAP as /home in ext3, set last 1-2 GB as SWAP.

Use dual boot.

---

### Post by Ali. on 2007-06-20
I'd marry most people around here given half the chance tbh. Helpful bunch of lads.

Cheers :)

---

### Post by dptxp on 2007-06-20
> **Ali. said:**
> I'd marry most people around here given half the chance tbh. Helpful bunch of lads.

Cheers :)

If you are a female then I am married.
If you are a male, well, will someone take me off this thread.

---

