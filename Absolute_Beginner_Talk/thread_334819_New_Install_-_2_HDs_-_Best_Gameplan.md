---
title: "New Install - 2 HDs - Best Gameplan"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by hey_ygbsm on 2007-01-09
Ubuntu/Linux Newbie.  Hoping to keep running windows for awhile...but, would like to 'stick my toes in the pool' to test the waters, so to speak. So, a Dual-Boot Linux/XP setup looks like the way to go.

Athlon XP vintage system with 2 x HDs.

Disk0 is C:\Windoze XP....200 Gb ( 2 x 100 Gb, FAT32 partitions)
Disk1 is D:\...120 Gb

Windoze XP currently resides on Disk0_Vol1.  Basic gameplan is to put Ubuntu on its own drive (Disk1) with XP/Ubuntu shared data in the 2nd partition on Disk0 (i.e. Disk0_Vol2). I'm looking for some help determining how many, reasonable size, file format & locations for the various partitions required for Ubuntu, Linux swap, shared files, boot, usr, profiles, etc.

Since I just re-installed XP and have loads of space, what are the 'Best Practice' guidelines for allocating space? 

Or, would I just be better off going to a removable hard drive configuration with a separate drive for XP and Ubuntu?

---

### Post by kidders on 2007-01-09
Hi there,

Since you have more than one hard drive, it makes no sense (in performance terms) not to use them all at the same time, so if it were me, I would spread XP and Linux over both your internal disks.

Just like Windows, a decision to spread an OS over multiple partitions, and what sizes to make them, is a very personal one ... but if you make the wrong decisions, you can always tweak your installation afterwards. :-)

You might decide, for instance, to do something like this...

[LIST]
[*]Disk0/Partiton0 - XP system
[*]Disk0/Partition1 - Linux system
[*]Disk0/Partition2 - XP applications
[*]Disk1/Partition0 - Linux /boot
[*]Disk1/Partition1 - XP pagefiles
[*]Disk1/Partition2 - Linux swap space
[*]Disk1/Partition3 - Linux/XP personal file storage
[/LIST]

... but it's all down to personal preference, really. My suggestion would have certain advantages (and, of course, disadvantages), but it's just an example.

---

### Post by hey_ygbsm on 2007-01-10
Thanks much for your response kidders. I forgot to mention that I already tried installing Edgy 'on top of' XP on HD0...GRUB apparently overwrote my MBR!! (hence, the purchase of a 2nd drive).  -- Mom & the kids were NOT happy with the week-long lack of internet whilst I re-formatted the HD and reinstalled XP.  Sooo, you can now understand my caution before a second attempt.  After careful consideration, I think perhaps I will re-group and revert to Plan B: Pull apart my kid's old computer...install a removable drive tray...and create 3 separate stand-alone loads for XP, Ubuntu & Edbuntu (since I have a few old, smaller drives available).  This will allow me to safely test drive my first Linux distro without detrimental impact to my other users.

Also, now that I've looked around here a bit, this thread more correctly belongs in the installation forum so others can use your sage advice on partition setup.

Appreciate the advice. Happy New Year.

---

### Post by kidders on 2007-01-10
Hey again,

> **hey_ygbsm said:**
> Thanks much for your response kidders. I forgot to mention that I already tried installing Edgy 'on top of' XP on HD0...GRUB apparently overwrote my MBR!! (hence, the purchase of a 2nd drive).I don't suppose going cold turkey and replacing XP with Ubuntu is always a terribly good idea!

Your bootloader will always rewrite the MBR on your primary boot device though, regardless of how many hard disks you have. But isn't that what you *want* to have happen?

You shouldn't have any trouble getting Windows and Linux running on the same machine. :-) Linux is very cooperative that way.

> **hey_ygbsm said:**
> Also, now that I've looked around here a bit, this thread more correctly belongs in the installation forum so others can use your sage advice on partition setup.Lol!

---

### Post by jvc26 on 2007-01-10
You should also be able to boot the XP from grub via a chainloader, the issues of not working usually occur when you install XP after and you get the windows bootloader which really doesnt like to boot up for anything else :)
Il

---

### Post by MindRiot on 2007-01-10
> **kidders said:**
> 
[LIST]
[*]Disk0/Partiton0 - XP system
[*]Disk0/Partition1 - Linux system
[*]Disk0/Partition2 - XP applications
[*]Disk1/Partition0 - Linux /boot
[*]Disk1/Partition1 - XP pagefiles
[*]Disk1/Partition2 - Linux swap space
[*]Disk1/Partition3 - Linux/XP personal file storage
[/LIST]


Wow,  that's an awesome partition scheme!

I have four questions:

1. How large should I make the Linux /boot partition?
2. How large should I make the Linux /swap partition?
3. If I determined partition sizes by percentage of total disk space, what would be a rough, but ideal percentage for each partition (excluding Linux /boot & Linux /swap)?

4. Can I assign the partition marked Disk1/Partition3 in your list as Linux /home and then move my Windows XP's  My Document and Settings folder to that partition.  That way both Linux and WIndows XP uses this partition for storing personal files?

---

### Post by kidders on 2007-01-10
Hi there,

> **MindRiot said:**
> 1. How large should I make the Linux /boot partition?Very small ... maybe about 32-48MB. It's primary advantage is that, after your system boots, you can mount it read only (or not at all) with /etc/fstab, preventing unintentional blunders (even by root) that might render your machine unbootable. Other possible reasons for a "/boot" partition include running Ubuntu off a USB device.

> **MindRiot said:**
> 2. How large should I make the Linux /swap partition?That depends on what you want to do with it. If you intend to hibernate your PC, you will need at least as much swap as you have RAM. Some recommendations suggest 1.5x your RAM. Using too much can damage performance, though. If you have more than one physical device, or need a *lot* of swap, it's worth considering making multiple swap partitions. You could, for instance, make 3x768MB swap spaces (1.5GB swap for 1.0GB RAM), two with priority 0 (ie used in parallel) and one with priority 1 (used only when all available swap is exhausted).

> **MindRiot said:**
> 3. If I determined partition sizes by percentage of total disk space, what would be a rough, but ideal percentage for each partition (excluding Linux /boot & Linux /swap)?Hard to say. For general use, try to allocate as much space as possible for personal files. You can always take some away later. Now that hard disks have gotten so big, I've gotten into the habit of leaving large chunks of disk space unallocated, for future use in whatever capacity I happen to need.

> **MindRiot said:**
> 4. Can I assign the partition marked Disk1/Partition3 in your list as Linux /home and then move my Windows XP's  My Document and Settings folder to that partition.  That way both Linux and WIndows XP uses this partition for storing personal files?Yep... that's a neat enough way of sharing stuff between two OSs. The goal there is to make it as easy as possible to swipe an operating system out from under personal data. In the event something goes drastically wrong at some point, you should, in theory, be able to reinstall both Ubuntu & Windoze from scratch, without having to worry about backing up personal settings, etc. ... because they're stored on a separate filesystem. Other advantages include being able to fsck your data without a LiveCD.

---

