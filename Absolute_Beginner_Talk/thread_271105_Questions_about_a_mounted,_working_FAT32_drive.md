---
title: "Questions about a mounted, working FAT32 drive"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-10-04
Hi all,

I mounted a backup drive after my NAS died.

I have been using Ubuntu for a couple of weeks, so I guessed from the go that Ubuntu was going to make the n00b read alot.

I got it working via the UbuntuGuide in the following means....

copied /etc/fstab to a backup, edited the file and added

/dev/hdc1   /media/backup_drive   vfat   iocharset=utf8,umask=000   0   0

and restarted the computer.

Great!... navigating to /media/backup_drive gives me access and most importantly, read-write access to the drive and it's old contents.

My questions are

1.  The drive shows up as UNTITLED in the "Computer" view of the file browser, and I can't rename it.  Any idea how I can (and before you answer, question 2 might be the reason...)

2.  The HDD shows up as a icon on the desktop called UNTITLED.  I'm guessing that Ubuntu thinks that it is a removable drive and that is why the icon is there.....

How do I correct this?? :-k 

Thanks everyone.

---

### Post by jd65pl on 2006-10-04
Anything mounted to the folder /media is taken as a removable storage point you could try making a folder some where else and mounting it there for example make a folder in your /home and mount it to that point.

J

---

### Post by DarkKoopa on 2006-10-04
Ha Ha...

Thanks....

Guess that's why I'm the n00b.

In my novice ways, I thought /media would be a sensible place to mount it.  /home it is, and /home works well.

Thanks again.

---

