---
title: "Can't install due to error?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by SamSlater on 2006-04-02
After partitioning my disks and during the install I get this error while it's copying packages to the hard disk.
Ok, I've burned the ISO at 4x and 8x on different makes of CD ROM. I've used Nero for the burning and tried other burning software. My cd roms are clean and my drive is new and doesn't have problems burning other stuff.

My partitioning is:

**/** ext3 (with boot flag) 224gb
**fat32** 20gb
**swap** 6gb

I first create the fat32 partition and mount it as** /**. I place it at the end of the drive as a logical partition. I then let the install create the **/** and **swap** partitions automatically and finish partitioning. I write the changes to disk and carry on with the install.

I get this message:


> _____________________________[COLOR="Red"][!!] Copy remaining packages to hard disk[/COLOR]_____________________________

Copying packages to hard disk failed. You may have run out of disk space in the target /var file system, or your CD drive may be having problems reading packages from the CD. Cleaning the CD drive or burning the CD at a lower speed may help.

Check /var/log/syslog or see virtual console for details.

<Go Back>_____________________________________________________________________<Continue>

Whats happening?

SamSlater

---

### Post by dcstar on 2006-04-02
[QUOTE=SamSlater]After partitioning my disks and during the install I get this error while it's copying packages to the hard disk.
Ok, I've burned the ISO at 4x and 8x on different makes of CD ROM. I've used Nero for the burning and tried other burning software. My cd roms are clean and my drive is new and doesn't have problems burning other stuff.

My partitioning is:

**/** ext3 (with boot flag) 224gb
**fat32** 20gb
**swap** 6gb

I first create the fat32 partition and mount it as** /**. I place it at the end of the drive as a logical partition. I then let the install create the **/** and **swap** partitions automatically and finish partitioning. I write the changes to disk and carry on with the install.

I get this message:




Whats happening?

SamSlater[/QUOTE]
Having two partitions with the same "/" mount point, I'd say.

---

### Post by Princey on 2006-04-02
Why mount the FAT32 partition as "/" ? / Refers to your root directory/partition so in essense, you have two root partions. I'd suggest you use the swap partition (A Must), split the 224Gb to 30 GB (mounting it as / or root as I previously explained) and the 194GB mounted as /home. Leave the FAT32 out of the picture for now. You can mount it afterwards to use as sharing files between Windows XP and Linux. However, if you don't dual boot, I see no reason for keeping the FAT32 partition as FAT32 partitions do not maintain file permissions.

My reason for suggesting a separate partition for /home is simple: home is where your personal settings and files go. In case of a system going awry and you have to re-install, all your documents and settings will be intact and not lost. Good luck.

---

### Post by SamSlater on 2006-04-02
Yes I mount a fat32 partitiion as ''/'' but when the system automatically creates the ''/'' partition it automatically sets the fat32 partition as 'Do not use' and is not mounted. Apparently it has to be done that way, at least it says so with [[COLOR="black"][COLOR="Sienna"]this[/COLOR][/COLOR]]("http://users.bigpond.net.au/hermanzone/p3.htm") installation guide.

Yes I will be dual booting and have XP on a seperate NTFS partition.

I'll try without the fat32 partition but I'm sure I already tried that with the same error.

Thanks,

SamSlater

---

### Post by SamSlater on 2006-04-02
No chance.

I again, downloaded the 'ubuntu-5.10-install-amd64' iso from a different mirror site and checked the 'md5sum' which was ok. I burned another blank cdrom @ x1 speed this time instead of x4.

I made sure all other partitions were deleted on my spare HDD and partitioned:

#1   primary   30.0GB   ext3   /          (with boot flag 'on')
#5   logical    213.0GB  ext3   /home
#6   logical    6.2.0GB  swap   swap

I write the changes to disk but I'm STILL getting the '*Copying packages to hard disk failed.*' error.
I've tried 'Guided partitioning', 'Manual partitioning', Creating seperate '/boot' & 'fat32' partitions, I've downloaded different 'iso' files from various sites, burned at x8, x4, x2, and x1 speeds and always checked md5sums.

I must have tried to install ubuntu over 20 times today but nothing. I've googled this error and found it mentioned on a grerman forum. After translating the discussion they tried everything as well with no success.

Even though I despise XP it looks like I'm gonna have to stick with it :(

Anyone else ever solved this problem?

---

### Post by Princey on 2006-04-02
[QUOTE=SamSlater]No chance.

I again, downloaded the 'ubuntu-5.10-install-amd64' iso from a different mirror site and checked the 'md5sum' which was ok. I burned another blank cdrom @ x1 speed this time instead of x4.

I made sure all other partitions were deleted on my spare HDD and partitioned:

#1   primary   30.0GB   ext3   /          (with boot flag 'on')
#5   logical    213.0GB  ext3   /home
#6   logical    6.2.0GB  swap   swap

I write the changes to disk but I'm STILL getting the '*Copying packages to hard disk failed.*' error.
I've tried 'Guided partitioning', 'Manual partitioning', Creating seperate '/boot' & 'fat32' partitions, I've downloaded different 'iso' files from various sites, burned at x8, x4, x2, and x1 speeds and always checked md5sums.

I must have tried to install ubuntu over 20 times today but nothing. I've googled this error and found it mentioned on a grerman forum. After translating the discussion they tried everything as well with no success.

Even though I despise XP it looks like I'm gonna have to stick with it :(

Anyone else ever solved this problem?[/QUOTE]

This may be by a long shot, but I really don't have all the specifics here so permit me to speculate a bit. Have you tried using your CD burner as the installation drive instead? Also, is the cddrive you use on the same ide channel with the hard drive? Somehow it seems either the transfer rate is slow or that the drive could be faulty. As a last effort, if your Windows installation is on a separate drive, I'd suggest you reformat the drive then partition it. Just guessing here.

---

### Post by r4ik on 2006-04-02
Might very well be the case my BenQ comby play's the same trick on me.
I noticed it when i could install on my other comp but not on this one using the same disk.

---

### Post by SamSlater on 2006-04-03
Thanks Princy,

Update:

Using ISO Recorder I recorded the .iso image from one of my cd-r's back to my hard drive (within windows) and re-checked the md5sum. It was exactly the same as the download so I know that the .iso image is burning properly.

I can't put the hard drive on the same IDE as the CD ROM as the hard drive is SATA so I'll reformat sda with the windows xp cd and then try again.

Maybe its the cdrom drive itself I dunno but recently I slipstreamed SP2 into my XP installation and re-installed XP with the SP2 using the same cdrom I have now so if it was the actual drive then wouldn't that have had problems?

Thanks for the info and I'll let you know how I get on.......

---

### Post by SamSlater on 2006-04-05
[QUOTE=Princey]This may be by a long shot, but I really don't have all the specifics here so permit me to speculate a bit. Have you tried using your CD burner as the installation drive instead? Also, is the cddrive you use on the same ide channel with the hard drive? Somehow it seems either the transfer rate is slow or that the drive could be faulty. As a last effort, if your Windows installation is on a separate drive, I'd suggest you reformat the drive then partition it. Just guessing here.[/QUOTE]


You were right,

I popped the install cd into my dvdrw and it installed first time. It's obviously the cdrom drive. Installed lots of stuff using the cdrom in xp and never had a problem so I guess the install cd is very picky on which drive it uses!

Thanks for the advise though!

SamSlater

---

### Post by Princey on 2006-04-05
[QUOTE=SamSlater]You were right,

I popped the install cd into my dvdrw and it installed first time. It's obviously the cdrom drive. Installed lots of stuff using the cdrom in xp and never had a problem so I guess the install cd is very picky on which drive it uses!

Thanks for the advise though!

SamSlater[/QUOTE]

Glad to hear that:-D ! On a side note, even under Windows XP it does that to me . After much searching and reading up on cdfreaks.com I've learnt that cd/dvd burners are much more dedicated and dependable readers. I can't exactly explain here without all the technical rambling that's not important at this point, but it does worth noting that if you have two drives and the CDROM fails, you're better off succeeding using the burner. Just for your information perhaps and someone else stumbling across this thread.

---

