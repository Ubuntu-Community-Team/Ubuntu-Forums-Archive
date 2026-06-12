---
title: "Automount RAID0 NTFS"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by workbench1 on 2007-11-11
I've read some topics of this subject, and I've managed to atleast mount my 2x250GB drives using ntfs-3g, and they pop up as one drive as they should.

I've mounted them in /media/raid

But, I don't want to do it manually everytime I start Ubuntu, hence my question. 
How do I automount the RAID0 NTFS partition when starting Ubuntu, without deleting its content, maintaining swedish charset and set the drive to read and write?

Thanks in advance

regards,

---

### Post by workbench1 on 2007-11-11
Bumping,

Would be glad for some help on this issue - many people have similar problems.

This is what I've done, to mount an RAID0 configuration:

sudo mkdir /media/<name of the raid disc>
sudo apt-get install dmraid
sudo apt-get install ntfs-3g
sudo dmraid -r
sudo dmraid -ay
sudo mount -t ntfs-3g /dev/mapper/<the disc, line2> /media/<mount point>

read/write seems to work

---

### Post by ryanlhjess on 2007-11-24
thanks

---

