---
title: "Edgy and the Wonky Install"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by warmotor on 2007-03-21
I resized the partition on my IDE storage drive (XP, XP swap and big games are on SCSI) and installed Edgy. Installed wine, made MP3/DVD/DivX work, enabled write to NTFS - apart from high-end games I'm using all my old Windows apps in Linux at about a 90% success rate. Super.

I decide to upgrade to a bigger drive.

After attempting to set up 3 partitions (160gig NTFS, 60gig ext3, 2gig Linux swap) and installing Unbuntu again - and failing several times (invalid drive compression? what?)... I finally get it installed and dual boot working again. Now I can't see any of my NTFS drives, SCSI or otherwise and streaming video over the network with Mplayer does not work.

Keep in mind the hardware configuration is exactly the same, except for the newer IDE drive. What could possibly cause the system to work flawlessly the first time but now is unstable at best?

Also, I've looked but can't find any way to force detection of my SCSI NTFS hard drives. So far it looks like they should show up in the Computer window and may need to be manually mounted, but what if they're not?

Haven't been this frusterated by an OS since FC5.

---

### Post by dstew on 2007-03-21
What is the output of lspci -l (entered in a terminal window)? This should show how your system sees your disks and partitions. Maybe we can get a clue as to what the problem is by looking at that.

---

### Post by warmotor on 2007-03-21
Rock. I've got a step one, sweet - thanks for the reply.

It'll be a couple days until I can physically get to that box again, when I do I'll post the results.

Thanks again for your time.

---

### Post by warmotor on 2007-03-22
OK, update.

I installed fuse last night and manually configured the NTFS storage drive I wanted to see. I could see the drive (and read/write to it) but I noticed that my add/remove programs option disappeared as well as the software sources options under administration. Wierd. I do what I need from the command line to get the ATI drivers installed and get dual monitors working and reboot.

OK, now GRUB is showing 2 installs of Linux. I'm coming to the conclusion that my computer has begun to hate me. Upon login, my drive is on my desktop and is now named after the actual volume info instead of the name I gave it when manually configured - and all of my menu items are back in place. Except for apparently having two identical installs to choose from everything looks kosher.

Normally I like to fight with a new distro because I end up learning so much, but ubuntu is supposed to be like Linux for the masses, right? This isn't any easier to get up and running than Fedora. For the life of me, I can't figure out why, after all these years, the Linux dev community hasn't figured out a way for me to download a file, click an icon and have it install a program with all the needed files. I shouldn't ever have to open a command line to install freaking video drivers.

Ok, now I'm just venting. Thanks again for taking the time to read my post, from what I've seen here over the past couple of weeks this is an awesome community. PEACE.

---

