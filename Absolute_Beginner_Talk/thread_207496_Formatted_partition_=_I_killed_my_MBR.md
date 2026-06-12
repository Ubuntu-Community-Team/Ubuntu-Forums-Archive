---
title: "Formatted partition = I killed my MBR"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ChiendeRue on 2006-07-02
Hello,

Please forgive me for being a klutz but here she goes:

I have recently installed Ubuntu Linux 6.06 next to Win XP as a dual boot system.

The computer contains 2 physical hard disks of 143 GB each:
HD 1: 	(1 partition)
		NTFS partition (143 GB) used by win XP

HD 2: 	(4 partitions)
		NTFS partition (120  GB) containing all my MP3 files
		+ the three Ubuntu partitions (file system, swap, Root) using 23GB

I wanted to format the 120 GB to a Mac Disk. I believed that this is the only way to have such a large partition readable/writable by both Ubuntu and Win XP (I have Mac-drive installed). Nothing would allow me to format the 120 GB partition to Mac disk so I deleted the 120 GB partition, hoping to create a Mac partition later.

PROBLEM: Now the computer will not boot up.

I can start with Ubuntu live CD but I have no clue how to repair the MBR.
Can anyone help a Linux illiterate please?

Chien,

Hanoi, Vietnam
(I do not speak any Linux yet, please write out instructions for your typical newly divorced from windows - happy but still a bit dazed8-[ )

---

### Post by confused57 on 2006-07-02
If you have the Windows install disc(not a recovery disc), you can boot up with it and enter into recovery mode by pressing "r", then entering   fixmbr
which should repair your Windows mbr.
If you don't have the Windows install disk, it can be done this way:

[http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot](http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot)

Read the instructions by Herman near the bottom of the page, which essentially explains how to create a Win98 boot floppy from bootdisk.com(this will work to repair an XP mbr).

---

### Post by ChiendeRue on 2006-07-02
Thanks Confused57!

Windows XP is back (after using the recovery by Windows CD). I'm using it now.

Now I would like to get my beloved Ubuntu 6.06.
I can see the three partitions (Ubuntu) plus the "unallocated" space on the physical hard disk.

How do I tell this machine that there is a Linux OS there?

---

### Post by confused57 on 2006-07-02
[QUOTE=ChiendeRue]Thanks Confused57!

Windows XP is back (after using the recovery by Windows CD). I'm using it now.

Now I would like to get my beloved Ubuntu 6.06.
I can see the three partitions (Ubuntu) plus the "unallocated" space on the physical hard disk.

How do I tell this machine that there is a Linux OS there?[/QUOTE]

Here's a way, if you have the alternate install CD:

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

Also, since you have 2 harddrives you might want to take a look at this:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

This last method would involve opening up your computer and switching the drive cables(if you're willing & able to do this) and may involve reinstalling Ubuntu.

At least this will give you some options...unless someone else may have a better solution.

Add:  another thread that may help:
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by ChiendeRue on 2006-07-02
Hey Confused57,

This information looks exactly like the thing I need. I'm impressed!
I'll start downloading the alternate install CD and go ahead with MBR/GRUB repair.

Ubuntu 6.06 is fantastic. Some applications are better than anything I could find in Win XP or Mac. amaroK for example!

The only thing missing to make Ubuntu a success here in Hanoi is "people who can repair the computer" for the average user. I am only a little bit more experienced than a layman. At least brave enough to try to fix my problems. Maybe that's the only reason why I have a problem...
Thanks to people like you, willing to help fast and efficiently, I can recommend Ubuntu to my friends.

Cheers

---

