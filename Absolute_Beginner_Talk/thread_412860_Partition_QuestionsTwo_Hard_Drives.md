---
title: "Partition Questions/Two Hard Drives"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by DarthWHO on 2007-04-18
My plan: Have my main OS as Feisty and run Windows in vmware for the few little apps that I may need here and there that won't run inside Linux

I have 2 hard drives (80 gb SATA and 120 gb IDE).

My question is this: What is the best partition setup to allow one drive to hold all my data (like /home) so that a reformat/re-install doesn't touch that drive? What is best for /swap, etc...?

Heck, my question may be even too noob to easily reply to...but, I appreciate your educated responses!

---

### Post by Wim Sturkenboom on 2007-04-18
As long as you have a seperate partition or disk for /home, you will not loose the data unless you make mistakes or something goes terribly wrong during the install. And as there's always a chance that that happens, backups are important.

Next partitioning schemes are very personal and depend on the use of the computer (desktop versus server)

Further
[http://ubuntuforums.org/showthread.php?t=410081](http://ubuntuforums.org/showthread.php?t=410081)
confused57 advises not to create a seperate home disk. I should have continued the discussion as I don't see how a seperate partition can influence the boot. However, you might not be able to login unless you have enabled the root account as root's home folder is not under /home.

I would keep the swap on the disk with the OS and applications. Reason is that when the system needs to swap, it does not interfere with your data processing. The old rule for swap is 2x memory size; I personally have added that it does not need to be more than 1GB (others say that 512MB is even enough).

You can create a seperate partition for /var. Reason for that is that log files might grow big and eventually your root partition (/) fills up and you will run into problems. If /var fills up, your system will keep on running and probably the only result is that logs are no longer created.
I only do this on servers.

If you use to many partitions, you start wasting space and it's nearly garanteed that you run out of space on one of them while the others are still nearly empty.

And last:
only use a part of your 1st disk for Linux. Don't use the rest till you want to try with another distro or with a newer version of your current distro.

So my solution
disk 1:1GB swap
disk 1:20GB linux (OS and apps)
disk 1:60GB spare
disk 2:120GB home
or
disk 1:1GB swap
disk 1:20GB linux (OS and apps)
disk 1:50GB spare (placing it here allows to still grow linux or home)
disk 1:10GB home (and create links to your data partition below)
disk 2:120GB data

---

### Post by clblanchard on 2007-04-18
Well, I have 2 sata drives.  I dual boot winXP and Feisty from a 120gig drive and that is where I keep my "/" and "/home" partitions.  The other drive is basically a big 250gig storage space that I share between the two.  I have my "swap" partition on this drive as well.  Doing this keeps the file system from having to read and write to the same disk when having to use the "swap" partition.  My "swap" is 512meg and I have 2gig system memory and I can't tell if it ever uses the "swap" partition.  Hope I helped you out.

---

### Post by DarthWHO on 2007-04-18
> **Wim Sturkenboom said:**
> 
So my solution
disk 1:1GB swap
disk 1:20GB linux (OS and apps)
disk 1:60GB spare
disk 2:120GB home


Thanks Wim, this is more what I'm looking for...I probably won't use that much "spare" space, but this is pointing me in the right direction.

Another question I have is this: When installing Ubuntu, and you already have a /home partition, are you able to reference that during the install? Or is it going to want to create one and you have to point it there later?

---

### Post by Wim Sturkenboom on 2007-04-19
I'm not sure about the installer (I only used it twice in 4 years for two different version of Ubuntu on two different systems). Either Ubuntu will setup the system for you (in which case it propbably  will not create a home partition but makes it part of the root partition) or you will always be taken to the partitioner.
If you have an existing /home partition, you need to point Ubuntu to it during the 'partitioning' phase of the install. So you have to do some manual work, else Ubuntu will create a new one

I suggest that you install twice. First a normal install. After that, create a few text files in your home directory. Next install again and see what happens. Afterwards you can check the files that you created (do they still exist).
That way you get a feel for it and if you run into problems one day, you will be more relaxed as you will think "no panic, I've done this before".
If you use this approach, don't worry to much about drivers or configuring the system completely after the first install as you're going to wipe it anyway.

Note:
although you can share home partitions between distros, it **might** give problems for the following reasons:
- different userIDs, so you can not access files created in one distro using the other one (this will usually not be the case if you share between 2 different versions of Ubuntu or maybe even Debian. Some distros start the userIDs from 500 and others start them from 1000.
- a newer version of e.g. Gnome might use a different file format (not likely but a possibility), so your GUI might look different or not work.
So that's where your spare space comes in handy (till you have figured out if they are the same or not and what the implication can be)

---

### Post by DarthWHO on 2007-04-19
Wim, thanks again! This is a great idea. I will do exactly that. I will do a couple of installs and test out how /home works. 

Obvisously by posting in the "Absolute Beginner Talk" that is exactly what I am. I really think that is the key to any new operating system, understanding the installation methods and options. As you said, play around so you know and are comfortable with how it works.

Originally, when setting up my system for dual boot, my main focus was simply ensuring my Windows systems still worked after installing Linux, Linux was my secondary concern. However, now that I haven't booted to Windows in over 3 weeks, I am more comfortable with the fact that Linux will be my main OS for a bit and I'm more willing to fiddle.

---

### Post by hendrix on 2007-04-19
can i steal this thread?

I've look around about my problem, but here I am.

I currently have XP Pro installed on a 36gb drive, and I have a slave drive that is 140 gb.  the 140 is partitioned a long time ago when i bought it, into 100gb and 40.  

I want to (if possible) use the 40gb partition of a drive to install linux, and see how i like it.  the 40 is empty, and I would not want to lose data on the 100 portion, or windows from the 36.  I backed up some files, but I have in total maybe 80 or 90 gig so backing up everything would not be fun.

when i get to the part of the install where i need to partition, i pretty much understand how to do that.  I want to manually do it.  tell me wher ei'm going wrong

"/"   will go to a portion of about 8 - 10gb for the OS
"/swap"   will go to a portion of about 1gb
"/files"   will be a seperate partition for everything else, all files / downloads etc...

can all these be NTFS?  I got an error after assigning those roots that said something about not being able to be NTFS...

Do i have the right partitions?  and in the screen where you select the drive/partition to the right, can i just make my 36gb blank and my 100gb blank so it doesn't do anything to them?

sorry if i don't make sense.

---

### Post by DarthWHO on 2007-04-19
Installing to that available 40 gig portion from what I understand shouldn't be a problem, will just be part of your multiple boot options in grub when you are done. However, the 40 gigs will have to be re-partitioned as you can't install onto NTFS. Once again, complete NOOB here, so someone more experienced may want to jump in.

So, basically, when installing and you get to the partitioning, you will delete the 40 gig partition (backup first of course) and re-partition this space for the linux partitions.

---

### Post by Wim Sturkenboom on 2007-04-19
@hendrix:
First of all, even if you have terabytes of data you need to make backups. You might do something wrong, the system might do something wrong or you might get a power failure at a critical moment during the partitioning and you might loose a lot if not all.
If you don't make backups, you should consider the data not to be important.

You need a home directory. You must try it out if Ubuntu will create one if you don't create a partition. I would suggest that you replace the /files partition by /home. /home is where your user data and user configuration normally is stored.

And as said by DartWHO, NTFS will not work.

And last:
don't steal threads; it will become confusing as nobody will know who is replying to who. So if you have more questions, I suggest that you start your own thread.

---

