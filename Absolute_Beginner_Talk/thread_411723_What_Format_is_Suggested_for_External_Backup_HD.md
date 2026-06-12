---
title: "What Format is Suggested for External Backup HD ?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-04-17
Hi --

I have a file server in the works and an external hard drive (usb) for the occasional backup.  How should I format this external hard drive ?  

I was thinking of using FAT32 because then, if the server failed, I could connect it to my Mac or Ubuntu system to retrieve my files.  However, is there any downside to using FAT as my format for the external hard drive that will be backed up by linux?

Thanks, 
Damon

---

### Post by chakkaradeep on 2007-04-17
It depends on your needs . The ntfs-3g gives good read/write support for NTFS formats. Anway  I would recommend FAT32 if you are going to use in multiple OS

---

### Post by anaconda on 2007-04-17
fat32 has that annoying 4GB filesize-limit, and because it hasn't got access rights you would have problems if you need files to have the same owners and access rights as they had on ubuntu..

I would use ext3, because it works in linux and windows (with fs-driver).. and propably also in MAC (dont know)

---

### Post by seetho on 2007-04-17
I use a 100GB USB harddisk for my backup and copying large files.  It was originally formatted under NTFS.  This is read-only under Ubuntu by default.

I partitioned it into roughly 80GB in ext3 and 20GB in FAT32.  The ext3 partition I use mainly for my regular backup, whereas the FAT32 partition I use to copy stuff to other OSes.

If I'm not mistaken, you cannot create FAT32 partitions of more than 32GB.

My Ubuntu crashed yesterday and I was able to restore my data from the ext3 partition.  You could just as easily restore your data from a fat32 partition.  I just don't bother about Microsoft stuff anymore since moving fully to Ubuntu several months ago.

---

### Post by frodon on 2007-04-17
FAT32 or ext3, the 4Go max file size FAT32 limitation isn't really annoying the only case to have this kind of big file is when you rip a DVD although you can split the image file so it's not a problem.
I have myself a 300Go external backup drive with a 250Go FAT32 partition and the rest in ext3 and till now it really fits my needs.

NTFS is really the worst solution because it's less good than ext3 and even if there's good ntfs drivers for linux now there's also good ext3 drivers for windows so it's better to choose the best file system ;)

---

### Post by thornomad on 2007-04-17
Thanks for your replies ... I didn't know there was a max file size restriction with FAT ... I do have media files (movies, etc) that are in uncompressed format (or saved as disk images) and some of them may top 4gb.  I will look at ext3 support for Mac ... I guess it makes sense to keep it ext3 since that is where it will primarily be used and FAT seems a little too limited (though very easy) to use.

Thanks.

D

---

### Post by anaconda on 2007-04-17
I think mac either has ext3 support or it is easily installable.. because mac is based on BSD (unix) 

But I haven't any experience with mac:s so dont really know..

---

### Post by bodhi.zazen on 2007-04-17
I would advise ext3

If your linux install fails you can easily access the data with any linux live CD or if needed from windows 

Ext3 on windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

ext3 is reliable and journaled.

---

### Post by catfishy on 2007-04-22
> If I'm not mistaken, you cannot create FAT32 partitions of more than 32GB

I've seen that with windows partitioner you can't go above 32 gb, but booting with acronis disk director or by using paragon hard disc manager (for windows), you can make a stable fat32 of any size; mine was 500 gb, but it got corrupt because of an I/O error, so today I am making a 500 gb ext3 partition and installing the driver mentioned above when I need to use windows...
i tried briefly but couldn't find any super-useful info on mounting an ext3 on a Mac... sorry

---

### Post by thornomad on 2007-04-23
> **catfishy said:**
> I've seen that with windows partitioner you can't go above 32 gb, but booting with acronis disk director or by using paragon hard disc manager (for windows), you can make a stable fat32 of any size; mine was 500 gb, but it got corrupt because of an I/O error, so today I am making a 500 gb ext3 partition and installing the driver mentioned above when I need to use windows...
i tried briefly but couldn't find any super-useful info on mounting an ext3 on a Mac... sorry

Thanks.  I want to get into linux full time anyway -- I suppose eventually I have to "take the plunge" fully.

D

---

