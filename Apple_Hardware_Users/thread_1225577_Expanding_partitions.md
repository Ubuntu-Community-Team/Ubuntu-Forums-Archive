---
title: "Expanding partitions"
date: 2009-07-28
forum: Apple Hardware Users
---

### Post by tripundra on 2009-07-28
Hi...

I would like to expand my EXT3 partition, to give more room for Ubuntu.
I currently 4 partitions.
1- HFS+ for MacOSX ( has 30gb free and gona need less as my intention is to move all documents ~10Gb to the midle partition)
2- HFS+ for Documents( mainly music actually as it's 40Gb and music takes 37 Gb) I have Itunes and Rhythmbox using the same space. gona change it to NTFS or FAT32 (haven't dicided but open to sugestions)
3-EXT3 Ubuntu ( currently 17 Gb and intending to go for 25 Gb )
4- Swap- ( 1.7Gb just in case I suspend the system, YES IT WORKS)


I can backup all my MacOsx to an external drive, the 2nd partition also.
But how can I move all the files in a EXT3 to an external drive or something in order to then reformat the drive with more space for ubuntu. 
What program would maintain all the structure so I just copy/paste it   like in Disk Utility?

---

### Post by gwydionwaters on 2009-09-25
you could use grsync, it's simple and gui. or just rsync. are you saying in your post that the swap partition needs to be a certain size to suspend? would that be why mine attempts but comes back right away? (mine is only 900MB currently)

---

