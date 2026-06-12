---
title: "basic steps for setting up dual boot - Ubuntu and XP?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by rocka on 2006-06-26
Hi,
Can someone please point me to a basic guide for setting up a dual boot system?
AFAIK, Windoze grabs all the space available by putting a hidden and unmovable file right at the end of it's partition, so I'm assuming the procedure would be to split the HDD into two partitions first, then install XP into one partition, and then Ubuntu into the empty space left... Have I got this basically right?

Also, I remember something from ages ago when I tried a bit of Mandrake that it couldn't see the windoze files - is that still the case with Ubuntu?

Ideally, I'd like to be able to work with the same files [mainly music, and some normal docs, spreadsheets etc etc] from both OS's.

Thanks for any advice...
8)

---

### Post by Jagot on 2006-06-26
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by glotz on 2006-06-26
You've got it right. Linuxes can read but not reliably write NTFS. You might want a shared FAT32 partition.

---

### Post by ajifans on 2006-06-26
You can install windows first without partitionining.

Then once windows is installed, you need to turn off the paging file.  You do this by rightclicking My Computer - Advanced tab - Performance Settings - Advanced - Virtual Memory, and then select 'no paging file'.

Then defrag your hard disk.

Once this has been done, boot up Ubuntu and go to install.  The installer should provided you with the option of resizing the Windows partition to give room for your Ubuntu partitions.


Edited Ubuntu partition to plural, as it's not advised to have less than 3 linux partitions (root, swap and home).

---

### Post by ajifans on 2006-06-26
As regards sharing files.  I have separate partition formatted with FAT32 for all the files that need to be shared.

However my main partitions are NTFS(XP) and ext3 & reiserFS (Linux) as FAT32 cannot handle files bigger than 4Gb, which will rule out some DVD iso's.

---

### Post by rocka on 2006-06-26
thanks for the replies, guys.

Unfortunately, things are a bit on hold for me atm, the motherboard has stopped seeing the HDD for some reason...

I got as far as the "prepare disk space" step in the wizard and then it just hung. I went and microwaved some rice and chili, and came back and it was still hung. Rebooted, and now in the bios it sees the drive but reports it as zero bytes size. ](*,) This is a brand new 200G drive... :-k 

I've just stuck an old 80G in it that I had lying around, but the same thing is happening there too.

I don't know - some bad coincidence maybe that the IDE controller has barfed just as I was installing Ubuntu??? :confused: 



Anyhow, it's half time in the football now and I have an 8AM start tomorrow so I'm going to give it a rest and think about it some more tomorrow night.

---

