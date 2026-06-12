---
title: "DVD archiving with Live CD"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by althouse420 on 2007-02-20
Windows XP took a dump on me yesterday.  I am using the Live CD to pull files off of my hard drive and burn them to DVD.  I then plan to reformat the hard drive and reinstall XP just to make sure that any viruses/problems are cleared.  My problem regards burning a file to DVD that is in excess of 4.7 GB.  The DVD writer tells me to reduce the size of the files being burned, which is impossible because its one file.  I do have access to another hard drive, however, it is NTFS formatted, which is problematic for Linux (to write).  I suppose I could find another hard drive and format it in FAT32, or partition off a small portion of my hard drive in FAT32, but both of those options seem like a lot of work for just a file transfer.  Does anyone know of any workarounds that don't involve writing to a hard drive (other than online backup)?

---

### Post by crispy_420 on 2007-02-20
Ok let me start by saying FAT32 will not be a good option. Since it is so old it does not recognize files larger than 4GB. So IF you can transfer the file over, it will be a jumbled mess.

Also there will be no way to burn the file either. Assuming you only have 4.7GB discs (formatted to really 4.4GB), it would be the equivalent of trying to put 2 liters of water into a 1 liter bottle. You may be able to get 8GB blank media, but they are not cheap.

So here are my options:

Try either [Bart PE]("http://www.nu2.nu/pebuilder/") or [Ultimate Boot CD for Windows]("http://www.ubcd4win.com/").

They both are like live CDs of windows. I prefer the UBCDWin as it has better default drivers (SATA, RAID, etc.). But on the downside you'll need an official XP install disc, so no factory install discs (the ones that give you no install options, like the ones that come standard with say a Dell, HP, etc.). Also you'll need a functional computer to build the disc, hope you have some friends close by.

If you have a second computer, try transferring the files. FTP?

A different live CD than Ubuntu. I like [Berry Linux]("http://yui.mine.nu/berry/"). It has great NTFS support. But you might look at distrowatch for a better option. My main tip, during boot, choose English or it will default to Japanese.

---

