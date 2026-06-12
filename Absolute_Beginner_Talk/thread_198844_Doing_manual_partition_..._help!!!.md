---
title: "Doing manual partition ... help!!!"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-17
First time to install an operating system, and that's why I have no idea of "partitioning" ... I have a hard disk of 30 Gb, divided into 2 drives "C" and "D" , I have Win Xp on the C, and I am planning to put Ubuntu on the D ...
the question gentlmen is , I am not planning to lose the stuff I have on my D drive, so While doing manual partiton during the install, does Ubuntu ERASE all the files and folders on the drive, and HAVE the drive for itself ???? :confused: :confused: .... having a back up is out of question , I know ....

Thanks ;)

---

### Post by aysiu on 2006-06-17
You should always have a backup.

What you're proposing to do should not erase your important data, but if you don't know what you're doing, you may accidentally do that.

Find a way to back up things--use 100 floppy disks if you have to. Borrow a friend's external hard drive or iPod. Back up.

That said, as long as you choose the right partition to reformat and mount as / and the other partition to *not* reformat, then you should be fine.

This tutorial explains all the steps:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by brentoboy on 2006-06-17
installing on "D"
(which, by the way, in lunix terms is hda2)
meaning hard drive "a" partition #2
hard drive "a" is your primary - master hard drive.

but, I digress,
installing on "D" will format it and make it completely blank and unusable from within windows.

copy everything you like from your d drive to your c drive before you start. and be very careful when it asks you how you want to partition your drives.  dont let it automatically take over the whole drive when it asks, do the manual partitioning and read everything it sais before you act.

---

### Post by aysiu on 2006-06-17
[QUOTE=brentoboy]
installing on "D" will format it and make it completely blank and unusable from within windows.[/QUOTE] At least temporarily. You can always install [FS-Driver](http://www.fs-driver.org) in Windows to be able to read/write Ext3.

Your NTFS Windows partition will be read-only from Ubuntu, though.

---

### Post by bruenig on 2006-06-18
What you want to do is during the install go to manually edit the partition table. Format the D drive as ext 3 and primary. Then when it asks you to set mount points, set the D drive as / and the C drive to whatever it gives you.

---

### Post by kpoole on 2006-06-18
[QUOTE=bruenig]What you want to do is during the install go to manually edit the partition table. Format the D drive as ext 3 and primary. Then when it asks you to set mount points, set the D drive as / and the C drive to whatever it gives you.[/QUOTE]

Don't take this advice.  You wanted to save what was on D and this will lose it.  

Make sure you have all your important data backuped up somewhere before you try anything like this.

---

### Post by aysiu on 2006-06-18
Whoa! You're right, kpoole. It seems a few of us might have misread the first post. I went back and read it. So the idea, I guess, would be to resize the D: drive and make space for Ubuntu. Then create an Ext3 partition out of the new space.

---

### Post by mourad on 2006-06-18
[QUOTE=aysiu]Whoa! You're right, kpoole. It seems a few of us might have misread the first post. I went back and read it. So the idea, I guess, would be to resize the D: drive and make space for Ubuntu. Then create an Ext3 partition out of the new space.[/QUOTE]

Wow wow hey guys , you have to slow down on me , I am a newbie here :D ... I really got confused, however what I am very sure of is " to resize the D: drive and make space for Ubuntu. Then create an Ext3 partition out of the new space" .... 
Yes EXACCTLY as you realized at last Aysiu , but I don't know what is the Ext3...

Could someone right this specific step in a " 1, 2, 3 way" ...

Thanks to all of you , and especial thanks to Kpoole ;)

---

### Post by mourad on 2006-06-18
[QUOTE=aysiu]At least temporarily. You can always install [FS-Driver](http://www.fs-driver.org) in Windows to be able to read/write Ext3.

Your NTFS Windows partition will be read-only from Ubuntu, though.[/QUOTE]

I really do not want drive D from inside the Windows to unstable and unable to read and write... I have very valuable stuff that I use daily ....
So after install FS-Driver, Would it be stable and able to read and write or NOT ??? As TEMPORARILY is not a very clear word for me ????

I have FAT32 for my Windows, by the way.

Thanks again Aysiu

---

### Post by aysiu on 2006-06-18
There are basically three filesystems that are relevant to new users (sure, other ones exist, but they'll just confuse you more--for now, we'll stick with three):

NTFS
FAT32
Ext3

Most installations of Windows XP, 2000, or NT use NTFS as the filesystem. NTFS is read-only from Ubuntu. There are some projects to try to offer read/write access from Linux to NTFS, but they're experimental at this point, which means you shouldn't use them.

Older versions of Windows (like ME, 98, 95) use FAT32 as the filesystem. You, apparently, have FAT32 for yours, even though you have XP. That's okay. FAT32 gets easily fragmented, and it also cannot hold files that are larger than 4 GB. It can, however, *natively* be read from and written to by **both** Windows and Ubuntu. *Natively* means that you don't need any extra software for this to happen.

Ext3 is the filesystem that Ubuntu uses. Windows XP cannot *natively* read from or write to Ext3. If you install [http://www.fs-driver.org](http://www.fs-driver.org) in Windows XP, however, you *can* read from and write to Ext3 partitions. It is stable, and I've used it numerous times. It's fine. It is *not* experimental.

I will repeat what I said before, though:

Back up your files.
**Back up your files**.
I'm not kidding.

I'd say 99% of the time you should be fine without backing up your files. You can just defragment your Windows partitions, resize one, make room for Ubuntu, create a new Ext3 partition, and be fine.

What happens if you happen to be that 1%, though? Well, unless you've backed up your files, you're screwed.

Back up your files.

And read this link, which I linked to before:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by raptros-v76 on 2006-06-18
aysiu. good way of stressing the importance of backign up.

a tip, (someone should probably explain this better than i can), its always a good idea to have a seperate partition for the /home, which is easy when you consider that ubuntu doesnt need much space for its data

---

### Post by aysiu on 2006-06-18
Oh, and to resize a partition, you just right-click on it, select **resize** and then select the new size. (You would, of course, have defragmented this in Windows beforehand.)

In the empty space you created, you right-click it and select **create new partition** and make it of filesystem type **ext3**.

raptros-v76 is right--you may want to create a separate home partition. For more info on partition planning, read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by ZeusABJ on 2006-06-18
I don't know Aysiu, do you really think I should backup my files? I think I'm going to just try resizing this 200GB partition with all my priceless un-backed up data on it and just see what happens.... Yeah, backups are for wussies that are too lazy to spend hours trying to restore lost partitions at the command line!!!

:grin: :grin: :grin: :grin: :grin: :grin:

YYYEEEAAHHH!!!

---

