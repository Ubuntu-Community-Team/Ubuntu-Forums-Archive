---
title: "partitionmagic says 'ext2 filesystem corrupt'?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by wallacek on 2006-11-24
Hi all
using Norton partition magic to resize partitions (never could get Gparted to download correctly and burn to cd right.)  I can see all my partitions as they are, correctly. When I try to resize ext3, the partition that ubuntu is using, I get a message "error 1200: ext2 filesystem is corrupt".

I don't see any ext2 anywhere. Can anyone shed any light on this?  My hdd partitions are as follows: 
NTFS (used by winXP)(primary)
ext3 (ubuntu)(primary)
linux swap- extended (logical partition)
if I should reboot into ubuntu (in XP at the moment) to fix this I can do so. 
thanks
karinne

---

### Post by Bachstelze on 2006-11-24
If I were you, I wouldn't trust PartitionMagic, especially to use on Linux filesystems... What's the problem with GParted ?

---

### Post by pandu.rs on 2006-11-24
may be your partition magic is old and hence does not recognize ext3. But ext3 is same as ext2, except that ext3 has journalling support (better reliability). so probably it is ur ext3 partition which is reported as ext2

---

### Post by karinne on 2006-11-24
okay- trying Gparted again. restarted, logged on w/Ubuntu this time. downloaded gparted liveCD. inserted blank CD. rt-clicked on liveCD, burn to disk. still no luck, seems one more wasted CD now. I can open it, but it's not booting anything from the CD- I see one folder (Isolinux, with several files, none of which launch anything) and gparted with our little barefoot icon- but with a red 'x' in the corner- says " couldn't display /media/cdrom0/Gparted".   help?  I've been at this for hours. I just want to resize my partitions!
thanks.

---

### Post by Bachstelze on 2006-11-24
You didn't burn the ISO correctly ;) [Here](https://help.ubuntu.com/community/BurningIsoHowto)'s how.

---

