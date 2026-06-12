---
title: "File system formats question"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-28
Hey all,

I have a 250GB SATAII drive that I've partitioned into two drives - a 60GB OS drive (C:) and the rest for data (D).  I installed a 2nd hard drive specifically for Ubuntu.  

The C: drive contains XP Pro and is formatted as NTFS.  I had the D: drive formatted as NTFS until recently.  It's my understanding that Linux doesn't like NTFS and that in order to access all of the stuff on D: I would need to convert it to FAT32.  So I moved all of my files off of the NTFS D: drive, converted it to FAT32, and began moving all of my files back to the new FAT32 D: drive.  The problem I've run into now is that I have a few files that are too large for FAT32 to work with.  Apparently FAT32 has a 4GB file size limit.  Anything over that and it doesn't recognize it (or in my case it tells me that there isn't enough space on the D: drive for the file to copy, even though there's over 100GB of space).

So now I'm trying to figure out the best way to allow Ubuntu to access the D: drive so I can get to my music files and movie files and at the same time be able to store the larger files on that drive (the larger files are disk images).

Any thoughts?  I'd appreciate your help with this.

---

### Post by mahy on 2007-02-28
IMHO writing support for ntfs from Linux is possible, but i've never tried that. Maybe someone else will direct to an appropriate howto. Another solution would be to break those large files into smaller ones.

Lastly, you could format it to XFS and have it accessible from Linux only :guitar:

---

### Post by Thrasonic on 2007-02-28
Thanks for the reply, mahy.  I suppose I could do as you suggest (splitting files) but of course I'd rather not.  And I really don't want to deal with another file system that only one OS can read.  I'm already struggling with NTFS/Linus.  Blah.

---

### Post by vigleik on 2007-02-28
Fat32 has a limit on the  filesize, as 2^32 byte (=4GB). In my opinion, you're better off keeping D: as NTFS, and install ntfs-3g to access it from linux. Even though the driver is still in beta, it's considered very stable. (But I take no responsibility for data loss.)

---

