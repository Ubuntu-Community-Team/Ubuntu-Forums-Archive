---
title: "Backing up large amounts of important data."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jmail524 on 2007-10-24
Hello everyone...

I have a question on the best way to backup my important personal files.  Like many computer users I have been accumulating docs, pictures, music, etc on my computer for many years and have just come to the realization that a loss of this data would be disastrous.  I am looking for advice on the best way to back it up.  Also, I hope this thread will serve as a good primer for other people as well.

I have so much data that I am going to back it up onto a external USB hard drive, hopefully, as long term storage.  But, because hard drives are not a proven medium for long term, I am looking for advice on how to help retain my backup as long as possible.  So I have a few questions:

1.  What file system should I use?
     EXT2? EXT3? FAT32? NTFS?  Are any of these better for backup/archiving.  Is one more easily recovered if data corruption or hardware failure occurred?

2.  Backup software?
     I know the location of all of the files I want to back up, so I can copy them by hand without any problems.  But, is there software that helps protect your data.  For instance, is there software that writes error correction information with the data so that there is a better chance of recovering the data is something has failed or become corrupted.

3.  Storage practices?
     I know that hard drives do not make the most reliable backup medium.  But I can't think of any other affordable way to backup hundreds of gigabytes of data.  Is the a way to store the drive in an environment that will help guarantee the best chance of recoverability.

and any other information you wish to volunteer will be greatly appreciated.

Thanks.


PS:  Maybe while YOU are reading this, you might want to backup you data.  I have seen so many of my friends say that they will backup tomorrow.  Unfortunately, sometimes (for data), tomorrow never comes.

---

### Post by bobplano on 2007-10-24
for backing up if you are in ubuntu, might as well use ext3. it is a journaling file system, so thats a plus. as for backup software i don't know, but you could use the rsync command. that's all i have to say, because i don't back up my data :). i just don't have anything worthwhile on this comp so no reason.

further reading about backing up [http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup)

---

### Post by dimbulb1024 on 2007-10-24
I back up to an external hard drive and think that way is basically a safe way to go. It is not on all the time, maybe a half hour a week, so longevity of the drive should not be a factor. (I did buy new hard drives for the external cases and didn't go with old ones.)

1. I don't know enough to answer, but I use ext3 which is the same as my laptops hard drive.

2. I use Siimple Backup available from Add/Remove under Applications. It has done great by me for the past 9 months. I exempt out my music and major video files which I manually copy to a second external. (it takes to long for full backups with 30 gigs of media files.) My full backups without the large media files are around 20-25 gigs.

3. I usually back up once a week. My settings have at least one full backup per month and I keep 3-4 months worth of backups on my external drive. And like I said before, an external hard drive that is only on when you backup should be a safe way to go.

---

### Post by aysiu on 2007-10-24
Why aren't hard drives reliable? They seem reliable to me.

I use an external hard drive formatted as Ext3 and back up with *rsync*

---

### Post by jmail524 on 2007-10-24
Thanks everyone for the replies.

It seems that EXT3 seems the be the unanimous choice and since no one has reported any problems, I will probably use it.

Also, thanks for the recommendations on backup software/commands.  I will look into each one.

As far as the reliability of hard drives as a backup medium.  I remember reading a quote from one of the hard drive manufacturers (can't remember which one) stating that a hard drive is not the best choice for long term backup storage.  They said that if the drive is not spun-up regularly, the bearings could seize prohibiting the drive from ever spinning again.  It was never stated how often "regularly" was and since I plan on keeping the contents up to date, I hope I will never see that problem.

Thanks for the suggestions.

---

