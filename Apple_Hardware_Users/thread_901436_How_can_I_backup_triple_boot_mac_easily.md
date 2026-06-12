---
title: "How can I backup triple boot mac easily?"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by Seaniesean on 2008-08-26
Hello, I was wondering if anyone knows how I can make a backup (of some sort) of a triple boot (mac osx hfs+, ubuntu and windows xp on ntfs) system.  

I was thinking along the lines of "install jolly GUI based application, click button with mouse, make cup of tea, ba-ba-bing-ba-da-boom, entire disk backed up to image" type solution. (no laughing at me).  I know you can use tar in ubuntu, various utilities in windows, and disk utility or superduper in mac.  Also, i know there are problems with the various filesystems like linux doesn't like hfs+, mac and windows don't like anything unless it's their own filesystem or fat, etc.  

So, what's the easiest way to do this?  Can anything backup an entire drive in this way, or do you really have to make backups for a particular OS using software for that OS?

edit- ha, just found "restore", maybe i'll try that...

---

### Post by dsmoot on 2008-09-24
I found this thread searching and I want something similar.  I have put a lot of work into a triple boot system and I'd really like a one stop backup.

It would have to be a Linux application (Mac can't read ext2, windows can't read the other partition file systems.

I'm envisioning a special boot CD + plus external drive that creates backup images for each partition's OS.

Am I crazy?  Does each OS have to do its own backup?  

David

---

### Post by BlackAura on 2008-09-25
I think it depends on whether you want to be able to easily restore the backups or not.

From Ubuntu, you could use a tool like Partimage to make an image file of NTFS partitions. You can restore the image back onto the original partition very easily.

The catch is that it won't work for HFS+ (Mac OS X) partitions, and there's no way to use Partimage to back up an Ubuntu system while it's running. You'd have to use a LiveCD for that.

You could make an exact image of the Mac partition. The problem is the image will be as large as the original partition, and you have to read the entire partition every time you want to make a backup.

All of that's doable from a LiveCD. You can basically image all the partitions using Partimage for Windows and Ubuntu, and making an exact partition image for Mac OS X. It'd be OK for a one-off backup, but there's no way to update these backups. You'd have to wipe them, and do them again. It could take hours.

As far as I can tell, the best tool for easily backing up a Mac is Time Machine, included with Leopard. Should the worst happen, just reinstall OS X, and when it asks to copy files from another Mac, give it the Time Machine backup.

You can use various tools (like TimeVault, FlyBack, or rsync from the command line) in Ubuntu to get the same effect, but they're not quite as easy to restore. You can't just give the backup to the Ubuntu installer, and have it copy the files over. I think you'd have to copy them manually. 

That wouldn't get the system setup either - just the files in your home directory.

As for Windows... I have no idea. I suppose you could just do a file copy from Ubuntu, but that'd also be kind of hard to restore.

---

### Post by seeker1458 on 2008-09-25
What about using something that does a byte-for-byte image of the disk.  You'd just be imaging 1's and 0's.  So If you found an application that could image all three ext3, hfs+, and ntfs...you'd be set.  Look at R-studio. I think they've got one that'll read all three.

edit: After reading up again...they've got apps that'll do ntfs, and ext2.  But they are TWO DIFFERENT apps.  Id still try to go the byte-for-byte route.

---

### Post by crapple on 2008-09-25
If you have an external hardrive you can search tucows.com for hard disk copy or something like that. I can't rember what it is called but it should be a zip with an iso in it and be freeware and say it is for copying hardisks. You burn that onto a cd. Boot from the cd and then it should create a copy of your harddrive with all three boots.

---

### Post by DGortze380 on 2008-09-25
Not as clean or as simple as you'd like, but I would just boot a live cd and dd the whole drive over to an external. every have any issues, just dd the whole thing right back. Ofcourse you'll have to then use something like rsync to keep incremental backups of your files, but that is simple enough as you can mount all of your drives in linux or os x and run rsync on all three with just one command.

---

