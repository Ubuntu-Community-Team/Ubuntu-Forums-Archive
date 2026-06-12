---
title: "Mount Point"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by jamillikan on 2007-05-21
I'd like to mount a Windows partition at a location other than /media/windows.  Particularly, I'd like to mount it at  /home/<username>/ASG.  Is this possible?
The reason I want to do this is so I can be in DOSEMU and output data to /home/<username>/ASG (where the ASG folder is actually a Windows partition mounted therein.)

When I try to output to just a regular ASG folder in DOSEMU, I receive the message:

Drive D:  does not exist or is not accessible.
It cannot be used for TAC cases/files.

Am I making sense here?

Hope you can help.

Joe

---

### Post by vtel57 on 2007-05-21
If you're trying to write date to a Windows NTFS partition, that's not going to work. Linux does not write to NTFS... normally. However, there is an application that is available that will allow it. Many Linux users will **not** recommend that you attempt writing to an NTFS partition, but it's your system. You can do as you please. See below:

[http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

[http://www.linux-watch.com/news/NS8947869272.html](http://www.linux-watch.com/news/NS8947869272.html)

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by jamillikan on 2007-05-22
Thank you for your reply, but the partition I'm desiring to mount at the point previously mentioned is a FAT32 Partition.  Does that help?

Joe

---

### Post by candtalan on 2007-05-22
you should be able to write ok to fat32 partition.

the mounting at boot (log in?) is controlled by contents of the file 
/etc/fstab

and looking at that will suggest what you need to aim at.

you will need to first create a directory named as you choose
/home/<username>/ASG
by the usual methods - it is in your user directory so you should not need admin rights (no need for sudo).

then you will need to edit the file fstab (with sudo - admin privilidges) to correctly include the new mount point directory and also comment out the previous one now not required. if the previous windows mount was fat 32 things should be pretty similar. if it was previously ntfs then you will need to use a fat 32 appropriate entry.

save a backup of fstab as it first existed, *before* your editing, just in case you need to go back.

good luck.

---

### Post by vtel57 on 2007-05-22
FAT32? Excellent! You'll have no troubles reading/writing to FAT32 from Linux. :)

---

