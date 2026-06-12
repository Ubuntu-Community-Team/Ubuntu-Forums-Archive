---
title: "cant see sata hard drive in windows?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by TooDamFast on 2006-12-20
Ive been using dapper for 8 months and decided to upgrade to edgy and duel boot with xp.

I just installed a new sata hard drive.  I formated it with ext3 and copied all my files to it (mp3's, avi's ect)

when I boot with windows I cant even see the sata hard drive with the disk manager.

any ideas?

---

### Post by po0f on 2006-12-20
TooDamFast,

Some people on the forums have had success using [this](http://www.fs-driver.org/) to get access to their ext3 filesystems on Windows.

---

### Post by TooDamFast on 2006-12-20
thanks for the reply and
that is what i was planning on using to read the files but I cant even see the drive.  I figured it would show the drive and that it would be a nonreadable format.  it doesnt.   the only drive listed under  admintools/computer management/storage/disk management is the C: (ide) drive.  the sata drive is not even there.

---

### Post by po0f on 2006-12-20
TooDamFast,

I didn't think Windows would care about volumes it can't read.  Did you install whatever driver came on the CD with your SATA drive?

---

### Post by holdinout on 2006-12-20
From what I've seen, Windows won't show you your linux drives or partitons. There are utilities however, to edit the drive. I can't name one which lets you acces files, but Acronis Disk Director showed ALL my partitons.

---

### Post by hal10000 on 2006-12-20
Windows can't see your linux-partitions (without additional software) but in windows disk management tool your sata drive should be seen if your win sata drivers are installed. Linux partitions (ext3, ext2 reiser ...) shold be seen as "unknown partition" or something similar.
 So I guess you have to install the windows sata drivers.

Even if you installed sata drivers (windows) you won't be able to access files on ext3 (or other linux partitions) without installing a windows tool that gives you access.
About how to download and install such a tool see here [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
I never tried this software, but although it is mentiones as an ext2 tool, I guess it doesn't matter if you have ext3, because ext3 is compatible with ext2.

But I suggest, if you want to access files from both operating systems to create a fat32 partition, which is read/writeable from both windows and linux without any additional tools.

---

### Post by TooDamFast on 2006-12-20
it fixed it self....  now I can see the drive as "unknown partition"  time to try out ext2ifs to see if it really works.  if it doesnt,  I just do the fat32 way (except it can handle files over 4 gig...)

Thanks for the help



Works like a champ!

---

