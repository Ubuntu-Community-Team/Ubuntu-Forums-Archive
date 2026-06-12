---
title: "Dual Boot Vista+Gutsy - GParted and OTher Troubles"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by lawnsheep on 2007-12-05
Hi All...First time posting.

This is my first time trying out any Linux distro, but I'm pretty literate with computers.

My university gives HP Compaq 8510w laptops out to all freshman with Vista 32-bit pre-installed.  Intel Core 2 Duo 2.2 Ghz, 2GB RAM, 120GB HDD.  

I've been trying to install Gutsy 64 on my computer, but have encountered problem after problem.  Searched the net for people with my laptop who have installed it as well, and found nothing useful.

Already booting from CD into live environment with "noapic acpi=off" as well as safe graphics mode and no "quiet splash" command.  I only get into Ubuntu Live half the time, but my computer always stalls at the same place regardless if I can boot fully or not.

I get "ATA1 ... buffer I/O error ... device sda ...", then a bunch of "soft resetting", "hard resetting", "COMRESET failed", "SATA link up 1.5Gbps"...This goes for a while, the kernel thinks the HD is bunk, everything loads and sometime the GUI comes up.  Other times the cursor blinks at the stage local boot scripts.

Kicker is that if I hit <ENTER> I get the ubuntu terminal and can type commands.

But the final crazy issue is this:  GParted doesn't see any partitions on my drive.  I have a 110 GB NTFS Vista partition and a 10GB FAT32 one for Ubuntu, yet GParted recognizes one 111.** GB unallocated space. Created the second one with diskpart.exe, not Disk Manager.  So there's the issue.  I've searched for about 2 days online and cannot seem to get past this final hurdle; I've decided to post to see if someone can put the pieces together.

Please no solutions of "Get rid of Vista, etc..."  Looking for a solution to dual booting with Vista already installed. 

Thanks for any future help.

---

### Post by philinux on 2007-12-05
i dont think ubuntu will like a fat32 file system as it does not support permissions like ext2 and ext3.

---

### Post by lawnsheep on 2007-12-05
Thanks Phil,

I tried to install on a Raw partition as well, did not work. I've read that the newest GParted doesn't like Vista's NTFS either, but it can see Fat32 easily.  The plan was to format to a Ubuntu file system from GParted once the partition could be seen.  Any thoughts on this would be great.

---

### Post by philinux on 2007-12-05
Welcome to the show by the way.

One thing is for sure you must use vista to make space for ubuntu using its own partition manager.


EDIT - read this.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3)

---

### Post by lawnsheep on 2007-12-05
Read that one before.  I created partitions that way the first time, which didn't work, so I tried the diskpart.exe (Also while in Vista, but is a console program, not GUi) which I heard is more robust.  Either way I partition, GParted still thinks I have one large, unallocated drive.  I've followed all of the tutorials, but they never seem to get the result i'm getting.  Thanks again.

---

### Post by philinux on 2007-12-05
One thing to do and this is a must is to defrag vista at least twice.

I assume you have the very latest gparted cd.

---

### Post by lawnsheep on 2007-12-05
That is something I haven't done (defrag).  I set up the scheduler to handle it every wednesday night at 3am, but I've been putting my computer to sleep at night, so I don't believe it has defragged.  I'll try that then I'll re-partition. 

As for GParted, I have whatever version is included with the 7.10 release.  I only ever access it through the Ubuntu Live Environment.

---

