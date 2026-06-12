---
title: "Numbers with Dual booting and partitioning"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-05-21
Hey everyone, I am venturing to do the dual boot...alas, I have more ram.. I would not know though what to choose for my selective space, so for the moment I am taking notes on this one.  My pc sais 30.1 GB with 768 Megabytes of Ram.  Now if I wanted to do say...300 MB of ram for Windows XO pro and then for Linux Ubuntu 6.10, < cuz I like that over Fiesty, using the rest , 469 MB of Ram, what would be the exact number in my choice here.  As when I have to partition the drive, what is the number solution GB to MB...MB to GB, because I dont know what its going to ask me and what exactly to type in there..

I want this, 300 MB of Ram for Windows XP....dual boot to....Linux Ubuntu 6.10 with 468 MB of Ram.

Thanks Sherri, I have been looking for an updated on-line tutorial with what it is I have in tact on Windows now without re-installing from the CD again.  I have an external hard-drive to save my things I just did not want to do all that, but can either way I suppose.

Thanks Sherri

---

### Post by Ferrat on 2007-05-22
What people mean when they say dual booting is not booting both OSes at the same time, you get to choose when you start your comp, what OS you want to start and both OS will use all the RAM when they are active but they will never be active at the same time. just Dual boot, the "name" can be tricky but it means you can boot either Windows or Linux but not both at the same time, you need to restart to switch to the other.

what you split up is the 30.1GB 
1GB = ~1000MB 

To be honest, how to split the harddrive depends on what you want to do

My suggestion would look something like this tho.
5GB - only core windows OS
5GB - only core Linux Os
20GB that you either share or split between the two.

---

### Post by hartz on 2007-05-22
> **delilahjed44 said:**
> Hey everyone, I am venturing to do the dual boot...alas, I have more ram.. I would not know though what to choose for my selective space, so for the moment I am taking notes on this one.  My pc sais 30.1 GB with 768 Megabytes of Ram.  Now if I wanted to do say...300 MB of ram for Windows XO pro and then for Linux Ubuntu 6.10, < cuz I like that over Fiesty, using the rest , 469 MB of Ram, what would be the exact number in my choice here.  As when I have to partition the drive, what is the number solution GB to MB...MB to GB, because I dont know what its going to ask me and what exactly to type in there..

I want this, 300 MB of Ram for Windows XP....dual boot to....Linux Ubuntu 6.10 with 468 MB of Ram.

Thanks Sherri, I have been looking for an updated on-line tutorial with what it is I have in tact on Windows now without re-installing from the CD again.  I have an external hard-drive to save my things I just did not want to do all that, but can either way I suppose.

Thanks Sherri

Hi Sherri,

What ferrat said is true, but I will try to be a bit more clear and explicit.  I will assume you know nothing of computers, and don't worry about it, if you already do understand this stuff, maybe someone else will find this post some day and get value out of it.

I want to explain to you the difference between RAM and DISK SPACE.

Both of these store data.
RAM is temporary - when you turn of the computer, all RAM is cleared.  Disk on the other hand is permanent(ish)
RAM is very very fast.  It is orders of magnitude faster than disk storage.
When you work on a document and you go to the "File" menu and select "Save", it copies the document from RAM to Disk.

One other distinction between (permanent) disk storage and (temporary) RAM storage is that the computer automatically knows what is what in RAM, but with Disk space, every file is explicitly given a "filename".  The files stored on disk is organized into "directories" (Windows calls them Folders, but it is the same thing)

While operating the computer needs to access the same data over and over millions of times per second.  This is why the very fast but temporary storage is required.

Now with that little lesson out of the way, re-read ferrat's answer.  The RAM in your computer is used by whatever operating system you currently have loaded (Some will say booted).  When you select Linux during the startup, Linux gets all the RAM.  This is temporary, and only until you reboot and then choose Windows, in which case Windows then get access to all the RAM ... temporarily.  In short: RAM (memory) does not get partitioned.

The Disk space however needs to be partitioned.  Windows and Linux uses disk storage differently, and needs to prepare the space that will be used on the hard drive through a process known as formatting.

In this regard, if you don't know how to partition your disk, use the following strategy.

[LIST=1]
[*]Boot into Windows and take record of how much free space you have and how much is used.
[*]Repartition the disk, leaving what is necessary for windows.  You will have to allocate at least 10 GB to Linux to make it practically usable, though you could get away with less in a cinch.  (Note that this process requires that you start off by de-fragmenting your Windows partitions though)
[*]After shrinking your windows partition, create new partition(s) for Linux.  Linux likes to have a part for the base operating system, a part for "swap-space", and a part for personal (user owned) files.  swap space should be at least equal to 1.5x RAM size to allow hibernating.  The balance can be divided between the base OS (root file system) and user-space (/home) any way you like, as long as you allocate some minimums.  I don't think any partition should be less than 3 GB.  the OS (/home) really doesn't need more than 10 to 15 GB Max.
[/LIST]

---

