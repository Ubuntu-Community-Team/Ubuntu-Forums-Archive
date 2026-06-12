---
title: "External Harddrive Help"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2005-12-24
When I first bought my external harddrive I was using Windows XP.  I formatted it as NTFS because that was the default and I never saw Linux or OS X in my future.  Now, it has all of my music, etc. and is just sitting plugged in as read only.  I don't mind that it is read only because I can access all the files I need fine, but is there any way I can add another partition to it so I can write to it?  I would like to be able to transfer over the music I download and such.  I know programs like gparted deal with this issue, but I have never used it.  I don't have another harddrive or a computer to plug it into at the moment that can write to it.  Any help?  I would really like to get my harddrive back in action.  Thanks.

---

### Post by bscbrit on 2005-12-24
Just to clarify - is this a dual boot computer or is it now just linux?

---

### Post by jbmalone on 2005-12-24
Just Linux.

---

### Post by bscbrit on 2005-12-24
I have seen several reports that seem to suggest that, if you are going to resize your disk using linux, you should defrag it first to avoid data loss and corruptions.  I am still not happy with the linux/NTFS combination.  If you haven't got access to a windows machine you will not be able to defrag.  There remain several possibilities.

Take the drive to a windows machine and do the resize there.

Copy the data off the drive (either to another drive [which I know you haven't got] or decide how much of it you really need and burn that data to DVD/CD).  Reformat the entire drive and then restore the data.

---

### Post by jbmalone on 2005-12-24
So no hope with resizing it using gparted?

---

### Post by bscbrit on 2005-12-24
I cannot say it will not work - somebody will come back and provide me with evidence that it worked for them.  But that might have been luck, or perhaps their drive was already reasonably defrag'ed.

All I can say is that, if the data is valuable, I wouldn't risk it.  If you search this forum or google, you will find plenty of horror stories.  True, those who succeed are unlikely to write to a forum about it, but it does show a sufficient failure rate to dissuade me from even trying.

However, wait a few days and perhaps someone else will come along with a solution or a sure-fire, never-fail way of doing what you want.  But don't hold your breath waiting.....

---

### Post by bscbrit on 2005-12-24
Its now Christmas Day (6 minutes old).  I'd better go to bed.  CU

---

### Post by jbmalone on 2005-12-24
Thanks for your help.

---

### Post by jbmalone on 2005-12-25
Does anyone else have an opinion on this?  I have seen people successfully use gparted on the board.  I would just like some other experiences and such before I try this.

---

### Post by bscbrit on 2005-12-25
jb - I have also found some threads on this forum describing how the method has been successful for them.  I'm sure that for some people it works - it simply depends on how valuable your data is.

---

### Post by plors on 2005-12-25
So, what do you want to do? access the existing ntfs partition? resize it and create a linux partition?

Anyway, ntfs read support is supposed to be stable, but i'm not sure about writesupport. Resizing ntfs should be quite safe using gparted. Of course it's always a good idea to make backups before fiddling with your partitions :)

cheers

---

### Post by jbmalone on 2005-12-25
Yeah, this is my idea.  I haven't looked at gparted so this is speculation on a couple of steps:

1. Defrag the whole disk, if I can.
2. Resizing the NTFS partition with my current data to however large it needs to be to keep the data on there safe.  I don't need to write to it or whatever, so I'm not worried.
3. Take the rest of the drive and formatting it FAT32 so I can use it with Linux and my Powerbook that I am getting soon.  

All that is on the disk is music, videos and some documents.  The drive is only four months old, so I don't think that the files are scattered over the drive, and as of now, the drive has NO system files from Windows or Linux.  I know that with the little I worked with PartitionMagic this is a kind of basic task, but I am just nervous because this is my only copy of some of this stuff, and I don't have a reliable way to backup 30GB of stuff.

---

### Post by plors on 2005-12-25
well, good luck and you don't have to defrag first. GParted will take care of that:D

---

### Post by jbmalone on 2005-12-25
Oh, nice.  I didn't know that.  Thanks for the info.

---

### Post by bscbrit on 2005-12-25
When you resize you _do_ write to the disk!

---

### Post by jbmalone on 2005-12-25
I will.  lol.  At least I hope.

---

