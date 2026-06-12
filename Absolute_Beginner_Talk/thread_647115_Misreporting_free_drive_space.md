---
title: "Misreporting free drive space"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by ScareCrow87 on 2007-12-22
Okay, I'm at my wit's end.  I am trying to use an external hard drive (formatted FAT32), 250 gigs.  However, even after I remove files from the drive, it's not giving me space back.  Ubuntu reports that only 95 gigs are beign used, but when I hit properties it shows only 899 megs left.  I plug it in to a Windows system and can see I have over half free, but in Ubuntu it's almost used up.  I checked the Trash folder and there's nothing there.  At this point I've got the drive almost cleared of anything I can, should have 160+gigs available, and can't even use 1!  Any ideas would be appreciated.  Only started using Ubuntu, so it's probably somethign simple I am just unaware of, but I'm giving up!  Thanks in advance

---

### Post by HermanAB on 2007-12-22
Try 'df'.

Anyhoo, using FAT on  a large drive is almost criminal.  For better results you should format it to either NTFS or Ext3.

Cheers,

Herman

---

### Post by sstusick on 2007-12-22
I was going to suggest cleaning the trash, but I see you've already tried that.

---

