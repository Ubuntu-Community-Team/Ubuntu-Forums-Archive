---
title: "Dual Boot Partioning Question"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by co.link on 2007-10-23
I'm about to rework my system.  I want to make Ubuntu a dual boot option on it, so that I can play with it a bit, While I still have windows for Steam and a handful of other programs.  

Here's the problem
I have a new drive that has 698 gigs of free space.  I want a 80 gig partition for Windows XP , a 68 gig chunk for the Ubuntu paritions and a 550 gig chunk for my "Meglomedia" drive.  
I've tried installing Ubuntu before.  I remember the first time trying to install Ubuntu, the easy options sounded something like Use Entire Disk (which sounds wrong for my goals stated above).  

Now, I plan to make a new install of windows then Ubuntu.  how do I do this so that the Dual Boot options work and end up with the partition sizes I want?  Also, is there a way to make Windows the default boot program?  I still plan to use that as my primary until I get more comfortable with Ubuntu.

---

### Post by ShahBucks on 2007-10-23
[SIZE="2"]Check out GParted- [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
You can go ahead and burn the ISO, boot from the disk and use this tool to setup your partitions any way you see fit! I like this tool b/c of its ease of use. You can set your windows (NTFS) partition to any size you like easily as well as your other partitions (ext3 or ext2 for linux, etc...)

I'd go ahead an install Windows first- tinkering with the boot loader on their end can be a pain if you install Windows last.

After the Windows install, go ahead and load your Ubuntu! You can edit the menu.lst file within the /boot/grub directory and set up that file to boot whichever OS you desire in any order you desire...

That's my quick input anyway... there's a good chance you'll get a slew of how-to's or links to other posts, but this seems to be the sure fire method that works for me every time.
Good Luck![/SIZE]

---

### Post by rsambuca on 2007-10-23
> **co.link said:**
> I'm about to rework my system.  I want to make Ubuntu a dual boot option on it, so that I can play with it a bit, While I still have windows for Steam and a handful of other programs.  

Here's the problem
I have a new drive that has 698 gigs of free space.  I want a 80 gig partition for Windows XP , a 68 gig chunk for the Ubuntu paritions and a 550 gig chunk for my "Meglomedia" drive.  
I've tried installing Ubuntu before.  I remember the first time trying to install Ubuntu, the easy options sounded something like Use Entire Disk (which sounds wrong for my goals stated above).  

Now, I plan to make a new install of windows then Ubuntu.  how do I do this so that the Dual Boot options work and end up with the partition sizes I want?  Also, is there a way to make Windows the default boot program?  I still plan to use that as my primary until I get more comfortable with Ubuntu.

If you are going to start fresh, the easiest method of doing this is to partition the drive ***before*** installing anything.  I recommend using the gParted liveCD, which has everything you need from a bootable CD.  You can [download the .iso from here]("http://gparted.sourceforge.net/").  

I would recommend a 80GB primary ntfs partition for Windows, followed by an extended partition of 68GB, which can be divided into 3 logical ext3 partitions:  10GB for '/', 1GB for swap, and 57 GB for /home.  The last Megapartition you can format ext3 or ntfs, your choice.

Install XP first, then Ubuntu.  For the Ubuntu partition, select manual partitioning and point the directories to the partitions you previously created.  

After installation, grub can be easily configured to make XP the default.

---

### Post by edwardTheGreat on 2007-10-23
> **co.link said:**
> I'm about to rework my system.  I want to make Ubuntu a dual boot option on it, so that I can play with it a bit, While I still have windows for Steam and a handful of other programs.  

Here's the problem
I have a new drive that has 698 gigs of free space.  I want a 80 gig partition for Windows XP , a 68 gig chunk for the Ubuntu paritions and a 550 gig chunk for my "Meglomedia" drive.  
I've tried installing Ubuntu before.  I remember the first time trying to install Ubuntu, the easy options sounded something like Use Entire Disk (which sounds wrong for my goals stated above).  

Now, I plan to make a new install of windows then Ubuntu.  how do I do this so that the Dual Boot options work and end up with the partition sizes I want?  Also, is there a way to make Windows the default boot program?  I still plan to use that as my primary until I get more comfortable with Ubuntu.

Look Here - Sounds perfect for what you want [www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

That is for an older version of Ubuntu but it enables you to keep using your Windows Boot Loader and blow away Ubuntu and GRUB if you decide it's not working for you... without affecting anything you currently have... Works a treat anytime I need it. I'll see if I can help where I can...

oh, if your Windows is Windows Vista, there are a few different steps when it comes to adding Ubuntu to your Windows Boot Loader...
Hope That Helps
Ed

---

### Post by co.link on 2007-10-23
what is '/' used for?
what is '/home' used for?
what is 'swap' used for?
Is 10 gigs enough for '/'?

I guess What I'm wondering is is 68 gigs enough space?  What's the optimal solution?  

Windows usually bloats with usage.  I don't know how Ubuntu runs, so I really don't know what sizes are good for these partitions.  I would really like to avoid the situation where three months from now I need to rework partition sizes, because I should have given X partition more space.

---

### Post by rsambuca on 2007-10-23
> **co.link said:**
> what is '/' used for?
what is '/home' used for?
what is 'swap' used for?
Is 10 gigs enough for '/'?

I guess What I'm wondering is is 68 gigs enough space?  What's the optimal solution?  

Windows usually bloats with usage.  I don't know how Ubuntu runs, so I really don't know what sizes are good for these partitions.  I would really like to avoid the situation where three months from now I need to rework partition sizes, because I should have given X partition more space.

68GB is tons and tons.  If you are storing your media files elsewhere, you probably can do with 10GB quite easily.

the root directory (simply referred to by '/') is where all of the filesystem directories are held.
/home is where your personal config files and settings are stored.  If you have this as a separate partition you can re-install if necessary without losing your setup.
swap is used if your RAM is insufficient for the programs you are using.  Since Linux is more efficient than windows, it isn't used that much unless you have small amounts of ram.

---

