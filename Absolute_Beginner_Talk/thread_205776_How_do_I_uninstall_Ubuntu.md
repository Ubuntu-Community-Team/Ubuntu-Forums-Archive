---
title: "How do I uninstall Ubuntu?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-06-29
My paritions are set up wrong on my drive and I want to start all over again. This time I want to partition my drive into three so that I can try out a couple of Linux distros and also have free space for windows XP to use.

Is it possible for me to have a couple of partitions I can install linux distros on and also have the larger part of the drive left over formated in NTFS for Windows use (large video files)?

The way my computer is set up is like this:

20gig HDD = Windows XP system drive
120gig HDD = Videos, music and other content
60gig HDD = Photos and personal documents
160gig HDD = This is my newest drive the one that has Ubuntu currently installed on it. It's currently set to dual boot with the 20gig drive that has XP on it. But I got the sizes wrong and LUbuntu is controlling 140gig of space and Window XP just sees the drive as unformmated. 

So how do I unintall Ubuntu and can I keep one larger partition NTFS? I have the Western Digital data lifeguard tools for Windows that lets you parition drives. But I haven't used it yet so I don't know if it lets you specifiy one parition as one filesystem and another as another.

---

### Post by Xzallion on 2006-06-29
Just repartition the drives.  It lets you specify the partition sizes.  then use windows to format the partition for windows, and use Ubuntu/any linux distro to format the partition for it.  Then just install to the appropriate partitions.
Windows usually doesn't see linux partitions unless you use the ext2fs drivers in windows.  what it is either seeing is a actual blank partition that you just need to format, or your swap partition(if your using the ext2fs drivers it will show your swap as a blank unformatted partition).

---

### Post by James R. Phillips on 2006-06-29
Use the ubuntu live-cd installer to boot your pc, and then start gparted.  You can delete the partition you installed ubuntu on, then create maybe 3 partitions: 1 1gb swap partition, 1 15 gb for /home, and 1 15 gb for everything else. You can leave the rest of the drive unpartitioned for now, until you decide what you want to do with it.  Then proceed with the ubuntu install, using the partitions you just created.

---

### Post by FuzZy2006 on 2006-06-29
Get into windows, format the linux partitions (ext3 and swap) and then, with the windows xp setup cd, go into the restore mode, there choose the partition where win is installed and then chose fixmbr. That will make you be able to boot to windows. Good luck

---

### Post by roxics on 2006-06-29
[QUOTE=James R. Phillips]Use the ubuntu live-cd installer to boot your pc, and then start gparted. [/QUOTE]

Where do I find gparted?

---

### Post by RRS on 2006-06-29
[QUOTE=roxics]Where do I find gparted?[/QUOTE]

System>Administration>Gome Partition Editor

---

### Post by roxics on 2006-06-29
Ok guys. 
Loaded up the LiveCD and ran gparted. I partitioned my drive into three parts. A 10 gig,  a 15gig (where I plan to reinstall Ubuntu) and the rest of the 124gigs are left open.

I then restarted the system, because Ubuntu told me I probably should. I came back into the LiveCD where I proceeded to install Ubuntu onto the 15gig partition. Since my last install of it was just wiped out from all my partitioning. 
I left the room for a while and came back to see the install had froze up at 25%. I could move my mouse but nothing worked, no menu's opened or anything like that. So I did a cold reboot of my system by holding down the power button for 3 seconds.

I went back into the LiveCD to try it again. This time things seemed like they were going good until it froze again at 84%. But this time menus and other things worked. I was even able to start up firefox and browse the web. I cold rebooted my system again and took out the LiveCD so I could just go to Windows for the time being. But after my system restarted I just got this error:

> GRUB loading, please wait
Error 15

...and my system just hangs. Won't boot into Windows or anything.

So I have two questions.

1. How do I get my system to boot up properly again so I can get to Windows (without having to physically pull out the hard drive I'm trying to install Ubuntu on)

2. How do I get the install to stop freezing and actually install ubuntu. I know it's not the CD as I installed it before with this CD no problem. The problems only started this time again.

Thank you so much for all your help.

---

### Post by roxics on 2006-06-29
Ok I finaly managed to get it installed but now it uses all of my 160gigi drive. So I'm worse off then I was before. It let me manually partition the drives but it didn't let me select them. OS I had to chose to erase the whole disk.

I'm going to have a find another way to do this, i need the bulk of this space for Windows.

---

### Post by roxics on 2006-06-29
I finally got things partitioned properly. Giving my 160gig drive a 20gig partition for Ubuntu, a 1gig partition for a swap drive (which it didn't let me use afterall) and the rest is left unallocated. I plan to format that remainder in Windows for NTFS.

Something strange happened however. This time when Ubuntu loaded up all of my hard drives were mounted on the desktop and I'm able to read them all. Even though they are NTFS drives. Why is that? It didn't do that the last time I installed Ubuntu earlier today. Oh well, that's good news I guess.

---

