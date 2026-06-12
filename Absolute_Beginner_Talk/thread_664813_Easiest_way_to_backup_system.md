---
title: "Easiest way to backup system?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by DVD-R on 2008-01-11
Hi Gang,
It seems to me that if I boot up on the install CD (live Ubuntu) I should be able to access an external USB hard drive and also access all of the files on the PC hard drive.  

If this is true, I should also be able to do some kind of really simple file command to make a complete copy of the hard drive onto the external drive, and within a folder.

Then if I ever need to, I should be able to restore the full system from from the files saved on external.

right???:)

---

### Post by freesitebuilder on 2008-01-11
This page has some info:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by LeAstrale on 2008-01-11
if you think in the way of ghosting your disc i would recommend Partimage which is a part of the system rescue cd.

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page) thats the link to its homepage.

---

### Post by DVD-R on 2008-01-11
THanks all!  :)
I have Acronis, but it looks like PartImage will be a better fit.
I don't want to have to install anything on the PC, which is required by Acronis.

I am downloading the rescueCD iso file as it comes with PartImage.
Then I will play with it.
It sounds pretty straight forward to make a ghost image from one drive to another, which is all I want to do.
Making backup and restore as easy as possible.
Big thanks!

---

### Post by DVD-R on 2008-01-11
So here is what I came up with.
I'm gonna re-partition the HD with about 5 gig as a secondary partition to hold the PartImage system shapshot file.
RescueCD boots up fine in the machine and I can then get PartImage up and running from it.

Don't know if the system will identify my external usb HD or not.
Will just go ahead and use the secondary partition.
Then if I need to, I can simply write-over the primary partition for a system restore.

Thanks!!!

---

### Post by gregcss on 2008-01-11
How did using PartImage go? I am looking to image my partition as well

---

