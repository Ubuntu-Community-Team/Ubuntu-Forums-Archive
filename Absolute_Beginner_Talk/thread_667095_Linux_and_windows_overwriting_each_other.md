---
title: "Linux and windows overwriting each other"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by mrthundercleese4 on 2008-01-14
I have a dell inspiron 4500 with a new western digital 500 gig hd that i have benn working on trying to get to dual boot for days.

here is the problem
When i install linux first wondows overwrites it
when i install windows xp first linux seems to mess up my boot and i get a blue screen error about windows xp mount not right.

also windows wont recognize more than 133 gigs of my hd formatted or not. it seems that if i setup linux first though it does recognize the full hard drive space in the gui.

Could it be the cd that came with my computer or do i need to leave a partition for boot space? does the position of the ntfs mounting matter?

on partitioning i have been doing 70gb windows, 70gb linux, 2 gig swap, and everything else one large fat 32 partition

Also the two os's are Ubuntu 7.10 and windows xp

---

### Post by logos34 on 2008-01-14
vista or XP?

---

### Post by swoll1980 on 2008-01-14
either your not partitioning the disk wright or both oses are on the disk but you cant boot them make your self a disk of partedmagic and grub google these and also google "how to dual boot" and also "how to use grub" and "how to use parted magic"  there are lots of walk throughs for this online. if you have questions after that feel free to ask

---

### Post by mr32123 on 2008-01-14
I think the problem is that you are not partitioning your drive before you install.  I suggest getting a good partitioning tool, you can get many free online, I'll let others post good free programs since I use the OnTrack Disk Manager that came with my computer.

Anyway, the simplest way to do this is to format your drive into two partitions.  One (NTFS) for your Windows, and the other for Ubuntu.  Then all you have to worry about is making sure to install each OS on a different partition and not get confused so you don't end up over writing it such as has been happening to you so far.

I think it is better to install Windows first from my experiences.

*******On a side note, I think it might be interesting, given your large hard drive if you could make three partitions.  The two for operating systems, and the third formatted as FAT32 to allow both systems to read and write files to a single partition.  Of course you can always use NTFS and then just get the NTFS "plugin" for Ubuntu.  Has anyone tried this?

Honestly I've always had trouble with dual booting from the same drive.  Then again I was just starting out with Linux at the time.  My advice is go and get another drive and install each on a different HDD, I think its safer too, just in case something does go terribly wrong, you'll have an OS backed up and won't have to keep reinstalling.

---

### Post by mrthundercleese4 on 2008-01-14
It's XP and windows starts to load the  i see the screen do you want to load in normal, safe or comand prompt mode and i get a blue screen trying to load windows.

---

### Post by swoll1980 on 2008-01-14
go to distrohunt.com search for parted magic download it make a disk boot it use the gparted to see how many partitions you have use the mount tool mount to mount booth partitions use the file browser to see what files are on the partitons if you borked your windows you will be able to rescue any file that are left over and burn them to a disc sounds like you may not have defragmented you drive before you partitioned your hard disk 
this could cause part of your win installation to be deleted if thats the case you will have to do a reinstall like I said use parted magic back up everything you can then post back

---

### Post by Sef on 2008-01-14
Go to [Gparted's site]("http://http://gparted-livecd.tuxfamily.org/") and download it from there.

---

### Post by mrthundercleese4 on 2008-01-14
well partitioning my drives with the partition editor on parted magic killd the windows installed 

I keep getting the message " a problem has been detected and windows has shut down to protect your computer. I might try partitioning again then installing the two os's maybe if i installed grub before windows too? btw where can I find a iso of grub?or does it not come in iso form.

oh and i defraged but being a fresh windows install there was not much to defrag. I ran the linux disck checker too and everything looked fine.

Thanks everyone for your continued support this has been such a frustrating project.

---

