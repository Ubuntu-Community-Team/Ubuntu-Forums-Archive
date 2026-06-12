---
title: "Simple backup, not so simple"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-11-19
Hi

Can anyone point me in the direction of a user guide/tutorial for Simple Backup. All I want, to start off with, is a simple reliable means of backing up my home folder. I've tried experimenting with Simple Backup, but I don't find it that intuitative.



Regards

Roger D

---

### Post by LLRNR on 2006-11-19
Hi RogerD, I think you can try:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) (if you want to backup a whole partition) or [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

HTH,

LLRNR

---

### Post by jkwarras on 2006-11-19
You can also take a look at the package hubackup. It backup your home folder.
[https://launchpad.net/products/hubackup](https://launchpad.net/products/hubackup)

---

### Post by RogerD on 2006-11-19
> **jkwarras said:**
> You can also take a look at the package hubackup. It backup your home folder.
[https://launchpad.net/products/hubackup](https://launchpad.net/products/hubackup)

Hmm... Yes, I've also had a look at this, but for some reason it doesn't seem to register my external hard disk as destination for the backup, and when I try to use a usb memory stick, which at least appears as an option for the "save backup to", I get the message:

Error mounting media. Make sure the media is not blank and retry.

There a crying need for a robust, well-documented, GUI-driven backup utitility in Ubuntu. I thought Simple Backup was it, but nobody seems to ba able to tell me how to use it. If I could work this out for myself, I'd be more than happy to post a simple user guide

---

### Post by mike984 on 2006-11-19
I wholeheartedly agree.  I have tried for the last few hours trying to get sbackup to work with my external networked hard drive.  I put in the [ftp://user:password@192.168.10.15/filename](ftp://user:password@192.168.10.15/filename) in and sometimes it goes through the motions and then end up with an unusable file or it just doesn't work at all.  A backup program must be reliable above all other things.  

I have come to the conclusion there is no simple backup program with a GUI available that works.  I shouldn't have to tinker with it to get it work.  Backup programs that work must be very difficult to write.

Sorry for my negativity - I'm just at my wits end.  All I want to do is have a backup program that can create a compressed tar file on a NAS drive that contains my home folder minus a few exclusions.  I haven't the knowledge of writing a script and I don't want a copy of my entire system. sbackup would seem to have all I need if I could just get it to work.  It could very well be me but like you said, it isn't documented and therefore hard to guess what I'm doing wrong. ](*,)

---

### Post by aysiu on 2006-11-19
*rsync* works great for me. If you need a GUI frontend, try *grsync*.

---

### Post by RogerD on 2006-11-20
> **mike984 said:**
> I wholeheartedly agree.  I have tried for the last few hours trying to get sbackup to work with my external networked hard drive.  I put in the [ftp://user:password@192.168.10.15/filename](ftp://user:password@192.168.10.15/filename) in and sometimes it goes through the motions and then end up with an unusable file or it just doesn't work at all.  A backup program must be reliable above all other things.  

I have come to the conclusion there is no simple backup program with a GUI available that works.  I shouldn't have to tinker with it to get it work.  Backup programs that work must be very difficult to write.

Sorry for my negativity - I'm just at my wits end.  All I want to do is have a backup program that can create a compressed tar file on a NAS drive that contains my home folder minus a few exclusions.  I haven't the knowledge of writing a script and I don't want a copy of my entire system. sbackup would seem to have all I need if I could just get it to work.  It could very well be me but like you said, it isn't documented and therefore hard to guess what I'm doing wrong. ](*,)


Glad to hear somebody else feels the same way - I thought it was just me.A user needs total confidence in a backup tool. Actually, Nautilus is a great way of creating a tar archive of your home folder on an external drive. You just right click on your home folder, select 'create archive' and away you go. The only problem is that I can't work out how I'd use this archive to re-create my home folder. If you right click on the tar file in your hard drive you get the option 'extract here'. That creates a folder, which, in  turn, contains your home folder. Unfortunately, you can't just drag this into home, so how is one supposed to use this tar archive to re-create your home folder in the event of needing to do a re-install?

I keep trying on this one.

Roger D

---

### Post by mike984 on 2006-11-28
I do not understand why Ubuntu does not include a backup program installed by default.  Every user should have a GUI backup program that works.

---

### Post by insane_alien on 2006-11-28
just copy the directories you want to backup to the storage media (compression optional) its not like M$ where you have a registry to contend with.

---

