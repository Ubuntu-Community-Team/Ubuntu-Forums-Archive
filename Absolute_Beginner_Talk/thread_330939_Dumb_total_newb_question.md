---
title: "Dumb total newb question"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-03
Hiya!  Before I go on, I have to let you know that my Master HD is damaged and I cannot re-partition it without totally formatting the drive first (I hope it will format... the MBT is all messed and so on and hours of googling, fdisk, and all kinds of things did not work).

Anyway... I want to back up all my data on an external HD.  I was just wondering what is the best way to do this from WITHIN WINDOWS (pre-formatting master and installing ubuntu).  If I format my external in EXT3 (or is there anyway to format a drive to XFS in windows) using partition magic, will I be able to just drop and drag files from NTFS master drive within windows?  Is it that simple?  I know about FS-Driver or whatever it is... is that required?  Will there be any filename character problems?  A friend once mentioned he copied files from NTFS or FAT32 or something to an ext3 partition and some didn't make the move because they had colons in the filename. 

Possibility #2:  I can format the external to NTFS.  I understand that I will have read-only access to the files.  What does this mean exactly?  I know I cannot modify/write, but would I be able to copy files from the external NTFS onto my Master Linux ext3/xfs drive and then have full rights to modify and use the file?  

I have 200 gigs of data on two NTFS drives right now using Win Xp and really want an easy way to incorporate them into a Ubuntu ext3/xfs system.  Speaking of that... should I go ext3 or XFS?  

Thanks,
Brian

---

### Post by raul_ on 2007-01-03
OR

possibility #3
Format the external drive as FAT and you will be able to access it from both windows and linux :)

---

### Post by darweth on 2007-01-03
> **raul_ said:**
> OR

possibility #3
Format the external drive as FAT and you will be able to access it from both windows and linux :)

Actually... I do know of that but I am allergic to FAT and would want to avoid if possible.  In this situation, I do suppose it is a very awesome option though (the external holding the files would be temporary until I can move them back and then reformat to something better)...


I really am allergic to FAT tho!!!  Right now I use Macdrive on a PC with HFS+ so I can share between my XP box and girlfriends G4 Mac.  Shoo FAT, shoo!  :) :)

---

### Post by dasunst3r on 2007-01-03
I am trying to get away from FAT32 myself.  I am truly thinking that EXT3 will be the better solution later on.

---

### Post by raul_ on 2007-01-03
Just use it to backup your data then get rif of it. You can access ntfs from ext and vice versa ;) you can always install the fs-drivers for windows and format it to ext3

---

### Post by djgrandmarquis on 2007-01-03
My external drive is formatted with ext3 and it plays very well with Kubuntu and XP. I just needed to install an ext3 driver in Windows:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

This way, my external drive preserves all my Linux time stamps and case sensitivity. The driver isn't open sourced, but it's free.

Good luck, hope that helps.

---

### Post by MrKlean on 2007-01-03
hiya ; )  If you mean the MBR is messed up.. you can fix it with the XP install disk.  There is an o[ption when the disk boots to hit "R" for repair.  When you get the command prompt.. do a 'dir".. you should see "fixmbr" there..it will fix the MBR of your disk.. maybe that will help you ; )

---

