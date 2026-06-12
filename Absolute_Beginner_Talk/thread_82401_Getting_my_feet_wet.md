---
title: "Getting my feet wet"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-10-26
Hello All,

I am going to try Linux once again, I previously tried Red Hat back in 98 with not much successes.

I just assembled a new machine and I installed Win XP Pro. When I installed it I partitioned the Maxtor 200GB Serial ATA Drive into 3 parts: 150GB NFTS for XP, another 35GB NTFS that’s empty now and the third is 15GB FAT32. I want to install the Ubuntu 64 bitPC version on the FAT32. How do I achieve this? Sorry I am probably asking the same question that has been answered 1000 times.

I am pretty good on windows and know my way around the inside of the case very well but Linux; so far it is Greek to me. I want to give this a serious try again almost 10 years later.

Any hints here?

Thanks
Bill

---

### Post by moffa on 2005-10-26
Well, I would suggest firstly adding a 2GB swap partition as well for linux.  When you are installing, do not accept the default partitioning, make sure it installs to the Fat32 partition.  I'm not sure if its recommended to use FAT32 as the main partition for linux, I use reiser.

The installer will automatically setup grub (boot loading program) and mount the ntfs file systems for you too.

Also, maybe download a Live CD and try it out first to check it out.  Keep in mind, the live cd is really slow in comparison to installing it.

If there is anything more specifc, ask away.

---

### Post by jrw6 on 2005-10-26
Short answer:  Don't install Linux on a FAT32 partition.

Long answer:  FAT32 doesn't support all the types of permissions Linux will want to change on files.  It won't work properly.

You should run the Ubuntu installer and have it make partitions in the free space.  You can use the FAT32 partition as something which both Windows and Linux can read.

Once again:  I STRONGLY RECOMMEND against installing Linux onto a FAT32 partition, and I doubt trying to would work anyway.

---

### Post by Micro Rotors on 2005-10-26
Ok, Then I should try to make that last one (15 GB) NTFS again. I read that if I wanted to later install Linux on a PC with Windows I should make a spot that was FAT32 for it. Will the partitioner in Ubuntu change that for me?

Thanks Guys for your input, I defiantly need it!
Bill

---

### Post by jrw6 on 2005-10-26
People will tell you to make a FAT32 partition because it's a partition type that both Linux and Windows can read.  It will be useful for sharing files between the two OSes, so you should probably have one.  How large you want it to be is up to you.  What you should do is make a FAT32 partition, whatever NTFS partitions you need and then leave some free space on the drive.  The Ubuntu installer should suggest a sensible set of partitions to create in the free space.

At least that's how the installer acted for me.  I can't say for certain though, since I run only Ubuntu on my own machine ;)
Just be careful when you run the installer that it isn't suggesting that you reformat one of your NTFS partitions.

---

### Post by paddyg on 2005-10-26
if i may add another few words...

jrw6 is right: never ** ever ** a Fat32---that's old win stuff---no journaling there. i use ext3.
It might be useful to have a /home partition as well
As for the swap, just 2x your ram (sombody even says just as much as your ram)
Install grub to the MBR, and always windows first, linux next.

---

### Post by SickTwist on 2005-10-26
[QUOTE=Micro Rotors]Hello All,

I am going to try Linux once again, I previously tried Red Hat back in 98 with not much successes.

I just assembled a new machine and I installed Win XP Pro. When I installed it I partitioned the Maxtor 200GB Serial ATA Drive into 3 parts: 150GB NFTS for XP, another 35GB NTFS that&#8217;s empty now and the third is 15GB FAT32. I want to install the Ubuntu 64 bitPC version on the FAT32. How do I achieve this? Sorry I am probably asking the same question that has been answered 1000 times.

I am pretty good on windows and know my way around the inside of the case very well but Linux; so far it is Greek to me. I want to give this a serious try again almost 10 years later.

Any hints here?

Thanks
Bill[/QUOTE]

150 GB sounds too big for the Windows NTFS partition unless you plan on installing a LOT of games/applications. Even then it sounds excessive. Keep in mind you will not be able to write (edit) any files stored here when you are running Linux.

Here is how I suggest you partition the drive:
**20 GB NTFS** primary partition for Windows + Windows applications
**10 GB EXT3** logical partition for Ubuntu (mounted as / )
**10 GB** unformated logical partition for testing other Linux distros
**10 GB EXT3** logical partition for Ubuntu (mounted as /home )
**1 GB** logical partition for swap
**all remaining space (~130GB) FAT32** logical partition for sharing data between operating systems

Here is the reasoning: 20 GB for Windows should be more than enough for the OS and the applications (remember, no user data here). Ubuntu will use less than 3 GB after a default installation so the 10 GB partition is more than sufficient for Ubuntu plus any new programs you might install. You might not think you need the blank partition now but it will be very handy if you ever change your mind. It is very easy to install a second copy of Ubuntu here if you want to test the development version or you could play around with another OS. It is a very good idea to mount the /home directory on a separate partition because this is where each user's preferences will be stored. If you ever need to reinstall Ubuntu (or switch to another Linux distro), just leave this partition intact and your settings will carry over. Linux uses the swap partition for virtual memory. This will be seldom used but is important to have. 1 GB will be sufficient, Linux cannot use more than 2 GB for swap. All of the remaining space will be formatted as FAT32 which will enable Windows and Linux to read *and* write here. This is where you should store your data (videos, music, word processing documents, pictures, spreadsheets, etc.).

Install Windows and only create the Windows NTFS partition during the Windows installation. After Windows is installed you should have about 160 GB of free space remaining. The Ubuntu installer will let you create the remaining partitions, format them, and choose how Ubuntu should use them: /, /home, and swap.

Don't let it overwhelm you. There are many people here willing to help if you get stuck.

---

### Post by moffa on 2005-10-26
[QUOTE=Micro Rotors]Ok, Then I should try to make that last one (15 GB) NTFS again. I read that if I wanted to later install Linux on a PC with Windows I should make a spot that was FAT32 for it. Will the partitioner in Ubuntu change that for me?

Thanks Guys for your input, I defiantly need it!
Bill[/QUOTE]

No... don't make it NTFS, make it ext2, ext3 or reiser.  Linux can read from NTFS partitions, not write (well not accurately).  If you are in doubt, leave it unpartitioned and set it up with the installer.

---

