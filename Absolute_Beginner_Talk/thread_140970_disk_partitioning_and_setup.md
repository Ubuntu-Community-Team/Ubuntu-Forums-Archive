---
title: "disk partitioning and setup"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by trorion on 2006-03-07
I need some guidance to make sure that my intention is going to work.

I have a dual boot computer W2K (for gaming and windows programs) and ubuntu.  I want my W2K programs to be accesible by Ubunto through Wine and I want to be able to write information to the programs.  For example, I like the "agent" news reader and I want to be able to access it from both W2K and Ubuntu.  I also want my saved documents (spreadsheets etc) to be accesible through both systems but I also want an area where my secure files are secure and my understanding is that if they are saved on a fat32 partition they won't be.

Next I want to be able to upgrade without causing problems with my installed programs so when I upgrade to dapper if there is a problem with it I can just re-install my breezy and not have to worry about all the programs being re-installed.

I have 1 large disk (80gb) and 1 smaller disk (10gb)
HDA
1-NTFS partition 6g for W2K
2-Fat32 partition 60g for programs (both *nix and windows)
3-ext3 partition 10g for ubuntu base install
4-ext3 partition 4g for "secure" documents on ubuntu

HDB
5-Swap partition 2g
6-fat32 partition 8g for multimedia

Now if that makes no sense then please help guide me!

- Install w2k on (1)
- Put the w2k programs folder and the /opt (and any other mounts that ubuntu uses for programs?) and /home folders on (2).
- Install Ubuntu on (3)
- Put an optional /home setup on (4) where I can put secure documents

- Put any multimedia files on (6)

OK, if it makes sense...how do I do it?

---

### Post by Ocxic on 2006-03-07
you should be able to run program from your windows partition using wine, but ubuntu or linux in general does not support writing to NTFS drives. there are ways of setting up write support but this is very limited, and you risk data loss.

Also you can't use a specific partition for both windows and ubuntu programs because of the way they install and everything ubuntu runs with must be an ext2/3,xfs,rieserfs or othe linux compatible filesystem, and windows requires a FAT or NTFS filesystem.
The only thing a FAT drive can be used for is to store/transfer data for use in between windows and ubuntu scince linux needs the attributes acciosiated with a journaling filesystem (permissions, ownership, etc...) which FAT32 does not support. not to mention the only filesystems windows can read/write is FAT and NTFS because Micro$uck is too cocky to write drivers to support other then native filesystems.

what do you mean by secure files???  The files on your system are only as secure as you make them no matter what filesystem there on, plop your hard disk into another computer and you'll always be able to read the files. if your worried about security then I would suggest encrypting whatever files you want to be kept secret/secure.

---

### Post by trorion on 2006-03-07
Thanks Ocxic!  Based on what you said it sounds like this would make more sense since I can't write *nix programs to a fat32 disk..

HDA
1-fat32 partition 20g for W2K.  Shared applications (agent/etc) and w2k
2-ext3 partition 10g for ubuntu base install
3-ext3 partition 40g for *nix programs
4-ext3 partition 10g for /home

HDB
5-Swap partition 2g
6-fat32 partition 8g for multimedia/shared files

Will that accomplish what i'm looking for?  To be able to run my windows applications via Wine and to have an easily updateable partition that doesn't risk my programs/documents?

---

### Post by Ocxic on 2006-03-07
thats much better but if you do this it will give you more data storage.
and your giving too much creadit to linux 10GB is plenty to install a ton of linux software, but 20 is better if your space consious:

HDA
1-/root  ext3  20GB
2-/home ext3 20GB  <--this will keep all of your personal settings, themes, and personal files if you have to reinstall/re-format.
3- fat32 20GB W2K   <--you can just run programs in wine from here.
4-fat32 shared files  (music,pics,movies,etc...)

HDB
1-fat32 8GB
2-Swap 2GB  <--the drive spins faster at the outer rim and the heads move less increasing performane thats why we put it at the end

---

### Post by ras on 2006-03-08
From what I've gathered from another thread: windows has to be installed first and must sit in the the first portion of the hard disk (1. in your setup).  Otherwise it won't boot.  So keep that in mind.

The thread: 
[http://www.ubuntuforums.org/showthread.php?t=141026&highlight=ntfs+partition]("http://www.ubuntuforums.org/showthread.php?t=141026&highlight=ntfs+partition")

There, ComplexNumber states:
"also, make sure that windows sits on the first part of the hard drive next to the MBR. if you install ubuntu first and put that at the beginning, then try to install windows so that it comes after ubuntu on the hard drive, windows will complain and just simply won't install."

Keep posted, I am very interested in how this turns out as I may be doing a similar procedure.

Best wishes,

ras

---

### Post by meborc on 2006-03-08
u might want to also read through hermans manual for dual-booting and PARTITIONING: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by trorion on 2006-03-08
Thanks OC!

I'm starting the process but going slow because I don't have a burner to back stuff up.  20g of programs takes a long time to copy!

[QUOTE=ras]From what I've gathered from another thread: windows has to be installed first and must sit in the the first portion of the hard disk (1. in your setup).  Otherwise it won't boot.  So keep that in mind.

The thread: 
[http://www.ubuntuforums.org/showthread.php?t=141026&highlight=ntfs+partition]("http://www.ubuntuforums.org/showthread.php?t=141026&highlight=ntfs+partition")

There, ComplexNumber states:
"also, make sure that windows sits on the first part of the hard drive next to the MBR. if you install ubuntu first and put that at the beginning, then try to install windows so that it comes after ubuntu on the hard drive, windows will complain and just simply won't install."

Keep posted, I am very interested in how this turns out as I may be doing a similar procedure.

Best wishes,

ras[/QUOTE]
Using Windows 2k and it's not nearly as picky as XP and it will install after XP, Linux, etc but it still demands the 1st partition.  I installed it after ubuntu with no problem (since my XP blew up and microsoft wanted $30 to send me new disks to replace my scratched ones after I paid $300 for the program I decided I didn't really need xp.)

I have a copy of "partition magic" that's very old and i'm working on cleaning up some free disk space to do backups to.  Wish me luck everyone!

---

### Post by trorion on 2006-03-09
Update (for those following)
OK, started the process.  I decided first to try to re-size the partitions and set up without blowing out all my data.  After that failed I started my clean install.

1st-
I used DSLinux to copy my important files to a backup drive (remember my re-size statement?  well it was a really bad idea to do that before backing up)

I've opted for this makeup:
HDa (it's a 140gb not 90gb)
partition 1:NTFS 40gb mounted at /dev/hda
partition 2:ext3 50gb mounted at /
partition 3:ext3 15gb mounted at /home
partition 4:fat32 20gb mounted at /dev/hda1
free space for 14gb
partition 5: linux swap

hdb (~12gb)
partiton1: 11gb fat32 mounted at /dev/hdb
partition2: 1gb swap

I know this gives too much swap but I wanted to try the raid0 swap system.  I may in the future blow out the ntfs and replace it with fat32 in which case I'll be able to modify the hda partition 4.

---

