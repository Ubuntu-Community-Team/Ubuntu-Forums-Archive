---
title: "stymied by partition install step on G4 450"
date: 2007-09-13
forum: Apple PPC Users
---

### Post by Jim Baker on 2007-09-13
Since I couldn't a partition set up for Feisty on the previous drive on my Mac G4 10.3.9,  I installed a new 80 gb Seagate. I'm running into the same problem where partitions need to be set up and there are NO INSTRUCTIONS HOW TO OPERATE THE SET UP UTILITY. This is the kind of thing that discourages us non-backenders from trying to use this thing, however great and economical some of the apps might be. The little details that are taken for granted are total showstoppers.

Specifically, I cannot figure out how to designate a partition size. I learned from a post that I should use ext3 file type and / for root (presumably without the quotes usually shown with it.) And I can select those. So I selected hda/hd2 for ext3 and root, but couldn't change the sector? size. It's stuck at 0.  Then trying to edit it, I got a field for file size with a 0 in it, and finally got it to accept more zeros but it won't take any other numbers. So that's useless.

 A nice little pop up wizard on how to do this crazy thing would REALLY HELP.

Will somebody teach me!
Thank you.

---

### Post by stmiller on 2007-09-15
This is for a dual boot system? You will have to create free space for Linux before starting the installer. The best way to do this is to wipe the disk and start over. (There are other ways, search this forum for how to resize HFS+ non-destructively).

So backup all data, then start the OS X install disc. But BEFORE starting the installer, let the disk boot to its startup screen, then pick the disk utility from the top menu bar. 

Under the disk utility, create 2 partitions. The first for OS X (hfs+ journaled) and leave the second partition for Linux as raw, unformatted free space.

Now install OS X as normal. Then put in Ubuntu disc and run the Ubuntu installer. It will automatically look to install in that free space. It will not destroy or touch your OS X partition unless you force it to.

But double check the partition changes of course, to make sure it looks okay before writing changes to disk. Then install Ubuntu as normal.

---

### Post by Jim Baker on 2007-09-15
Thanks, ST:
I would like to run a dual boot with Mac OS X, but what I'm starting with is a blank (2nd) hard drive with almost total free space and no installed software or files, other than a few k for making the disk capable of running OS 9. 

Also, I used iPartition to create two small partitions, using menu choices from iPartition for Linux Swap (250 mb) and I think Linux ext3 something (2 GB) for root. The remaining 70 + GB shows as "free space," but Feisty installer doesn't seem to know what to do with that.

So you're saying I don't need to create those little partitions for SWAP and Root, that Feisty installer will do it. So far, as far as I've gotten is the spreadsheet-like partition screen that tells me to set up those partitions—that it "can't install because it needs a small swap partition (250 mb) and a root partition (minimum 2 GB). That's where I get stuck because it's not clear how to define those sizes, or which of the many blocks with different names to use. 

But I'm going to try starting with a fresh wipe, totally blank 75 + GB hard disk, divide it in half in Disc Utility, then again try to install Ubuntu. You seem to know that this works, so I'm hopeful! 
 
   JB

---

### Post by Jim Baker on 2007-09-15
Installed Feisty on my G4 450, but had to completely wipe the disk and create a disk map in iPartition to get it all into "free space." With only partial free space, Feisty installer couldn't get beyond Step 4 of the installation sequence. Why? I kept getting "...probably due to not enough free space on disk." Unless I overlooked something, Disc Utility wouldn't create free space, it would create undedicated space but not free space. Not sure why or even if I explored all possible ways to do it.  I will do the process again to confirm.

Still only have a singe boot system on that drive and would like Mac OS X on it as well. Will OS X install in all that 74 GB of dedicated space? We'll see.

JB

---

