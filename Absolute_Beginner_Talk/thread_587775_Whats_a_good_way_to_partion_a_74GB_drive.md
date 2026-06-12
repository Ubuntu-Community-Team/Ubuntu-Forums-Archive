---
title: "Whats a good way to partion a 74GB drive"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-23
I'm getting ready to upgrade to Gutsy and i was thinking that I might use the CD and do a fresh install just to be clean and because I have heard a few negatives bout pressing the upgrade button.  I currently run a dual boot set up with linux on its own eSATA drive.  I would like to receive a recommendation about how i should partition this 74GB disk.  I would like to be able to see data on the Linux drive from windows for the area that I will store data.  My data will mainly consist of movies (avi) and mp3's with a few office documents.  Any suggestions will be appreciated.

Thanks in advance,

VC

---

### Post by amlucent23 on 2007-10-23
well... there are two ways to do it. The first I believe to be the simplest and most desirable for me.

I would think you would prefer to partition about 15 gigs of the 80gb drive as ext3 and mount as "/" then mount the rest ext3 as "/home".  Then next time you boot up windows just install [this ext file system driver for wndows]("http://www.fs-driver.org/faq.html"). this would ensure if you decided to reinstall ubuntu at a later date you would simply not format this partition and all of your personal settings would stay in tact. Sort of like a automatic backup.

or you could instead make the "/" partition a bit bigger say an extra 5-10 gb (to hold your data that you normally put in /home) and do the rest fat32 and mount as say "/data" you would of course be able to see this without installing anything extra on windows.

in the end its all a matter of your needs and your preferences.

---

### Post by Sef on 2007-10-23
> 
I would think you would prefer to partition about 15 gigs of the 80gb drive as ext3 and mount as "/" 

Actually 8-10 GB for / (root) is just fine.  Maybe 1 GB swap.  The rest would be home.

---

### Post by videocheez on 2007-10-23
> **amlucent23 said:**
> well... there are two ways to do it. The first I believe to be the simplest and most desirable for me.

I would think you would prefer to partition about 15 gigs of the 80gb drive as ext3 and mount as "/" then mount the rest ext3 as "/home".  Then next time you boot up windows just install [this ext file system driver for wndows]("http://www.fs-driver.org/faq.html"). this would ensure if you decided to reinstall ubuntu at a later date you would simply not format this partition and all of your personal settings would stay in tact. Sort of like a automatic backup.

or you could instead make the "/" partition a bit bigger say an extra 5-10 gb (to hold your data that you normally put in /home) and do the rest fat32 and mount as say "/data" you would of course be able to see this without installing anything extra on windows.

in the end its all a matter of your needs and your preferences.

Are you saying that the file at the URL that you gave me will allow a windows PC to see ext3 files?  If so, would i be able to move files (data) back and forth from Windows to Ubuntu?

Thx in advance,

VC

---

### Post by misfitpierce on 2007-10-23
I would say this

1.5GB swap
Rest to /

OR

1.5GB swap
10GB to /
Rest of HD to /home

 I choose to just allocate all to one spot but I usually burn my files to disc or put on SD card to backup when reinstalling etc. Allocating HD space to home manually can ensure no loss of data if you mess system file up and have to reinstall root. Safe way to do things I suppose.

---

### Post by markp1989 on 2007-10-23
i have the same size harddrive in my desktop,  i have set 

10gb for windows i only use windows for printing , you may need a bit more if you want to use it properly 
8 gb /
0.5gb swap mite need changing depending on amount of ram you have 
rest for /home

---

### Post by videocheez on 2007-10-23
> **misfitpierce said:**
> I would say this

1.5GB swap
Rest to /

OR

1.5GB swap
10GB to /
Rest of HD to /home

 I choose to just allocate all to one spot but I usually burn my files to disc or put on SD card to backup when reinstalling etc. Allocating HD space to home manually can ensure no loss of data if you mess system file up and have to reinstall root. Safe way to do things I suppose.

What does 10 GB to / mean?  What is the slash?

---

### Post by mivo on 2007-10-23
The slash is "root". When you are asked to enter the "mount point", the slash is what you type in. I also believe that 10 GB for /, the rest for /home (this is the mount point for the second partition), and 1-2 GB for swap. The advantage of this partition scheme is that you can very easily re-install or upgrade cleanly without losing your personal files and settings (which are kept in /home).

Think of / and /home as something like C: and D: in Windows. It is not exactly the same, since / really means "everything besides /home" in this scenario, but it will help you to unterstand the concept more easily. It is not harder than the system Windows uses, just different at first. :)

---

### Post by spur on 2007-10-23
The '/' signifies the file system start so its the main install area.
If one of your drives is an ide put your main partitions for all your oses on that. Grub can complain and you end up with error 21 if you put boot information on a sata drive if you have a mix of drive types.
I would recommend having partitions for /boot for boot info /home for user files and / for the main install. I have done similar with winxp as well. It does make it easier if you have to install and you can have the /home partition on any kind of drive.
Also you don't need a fat32 partition if you want to share with win anymore as Gutsy comes with read/write to ntfs.

---

