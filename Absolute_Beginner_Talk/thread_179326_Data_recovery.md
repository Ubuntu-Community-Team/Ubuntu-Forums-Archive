---
title: "Data recovery"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-19
Hi, I had my /home on a seperate partiton to my root file system.  Somehow (possibly human error I dont know) all my data from the /home partition is gone.  

I have no installed a copy of dapper onto some unpartitoned space I kept back.  My partion (hda3) which held my /home directory is untouched and unmounted at the moment.  

The problem is that I am unable to find a data recovery program for linux.  I really can't believe that it is possible that I will have to reinstall windows just to do this relatively simple task.

Testdisk appears to be useless for the purpose of recovering data - its only capabilty appears to be to restore a partiton table, but it is my actual data that has gone, not the partition.  

Can anyone suggest anything which is free and runs in a linux environment?

---

### Post by aysiu on 2006-05-19
Data recovery meaning that it's damaged and you want to look at the raw data?

Or do you just want to know how to mount the drive so you can copy the files off it?

---

### Post by skippy81 on 2006-05-19
Well the partition is mountable, but it appears to be completely blank.  I really can't figure out what has happened to all the stuff on it to be honest.  I mounted the partition in question and ran an ls on it, no files shown.  The gnome disk manager is showing it as having 5 gigs of stuff on it 8)  It should have more like 15 gig of stuff on it I believe.  

I tried test disk, it had no feature for scanning the sectors for files tagged as deleted.  Im starting to think that the design of ext3 simply doesnt allow for such recovery, it looks like if you lose the file tables you are stuffed.  

I have backups of most of it anyway, but it does seem worrying to me that ext3 is pretty much fatal to lose data on.  I might use a fat partion for backing up stuff in future.  On the bright side, the data I lost was actually windows data I had copied over before I deleted windows, so I will have quite a good chance of recovering it from the Fat partion.

---

### Post by aysiu on 2006-05-19
I don't think it's Ext3's fault, as I've never seen this happen before (i.e., it's not a common problem).

Have you tried mounting it and using ```
ls -a
``` instead of ```
ls
```? If you add the *-a* option, it lists hidden files and folders as well.

---

### Post by Sef on 2006-05-19
> I tried test disk, it had no feature for scanning the sectors for files tagged as deleted. Im starting to think that the design of ext3 simply doesnt allow for such recovery, it looks like if you lose the file tables you are stuffed.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by skippy81 on 2006-05-20
Thanks for the help guys, I am sorted now.  Well its good news for me.  Im going to post what happened incase anyone comes across this thread in a search.

**The incident:-**

Basically I used to have all my media files (movies and music) stored on a 80gb Fat32 patition at the end of my drive.  When I deleted windows, I installed dapper at the start of the drive and then copied the fat32 data onto an ext3 partiton.  I then deleted the fat32 partion, set it up as ext3 and installed an other copy of linux on it.  

Then one day I noticed that all my media files which I had copied to (and had been using) from the ext3 partion were gone.  I can only imagine that I somehow ran a delete on the ext3, since ext3 is considered very reliable.  Since I keep my PC on 24 hours a day, I could have actually deleted the data at any time. 

**Recovery:-**

My friend runs a repair shop, I used his open box with Ontrack Easy Recovery Pro to get the data back.  He assures me that a free utility such as PC Inspector would have attained the same result, just not as quickly. 

Rather amazingly I was able to recover all the data from the old fat32 partition, despite the fact that it'd had another OS installed over it.  

As the for data on the ext3 it is gone for good.  Googling has indicated that once an ext3 filesystem regards a file as deleted, you will never get it back. (Although chunks of text can be recovered if you know what you are looking for).   


**Conclusions:- **

Anyway the lesson to be learnt is:
1) keep backups
2) once you delete data from an ext3 partition you are never getting it back in anything other than a text format (media formats will be lost)  
3) fat32, although slow and annoying pretty much guarantees that you will get data back if you delete it, providing you don't defragment or write lots of data to the volume.  
4) the same goes for ext2, data can be easily recovered.  
5) ext3 is actually a poor filesystem for anything except a root system, while it is good for protecting the integrity of your data it has no safeguard against user error.  If you rm -r a ext3 partition you are stuffed.  The same operation on a fat32 or ext2 system can be reversed.  

As a result I have decided that while ext3 is good for a root filesystem, it is a bad idea for any partition which you use purely for storage (at least in a home user environment).  Ext2 and fat32 are far better choices in this respect, since you will ALWAYS be able to recover deletes.  Both Ext2 and fat32 data can be recovered with free software in both linux and windows.  Don't make the mistake I did and think your data is safer from accidental deletes on ext3 than on fat. 

Oh and one last thing, **make use of file permissions**. Why not set all your media data to read only?  The main thing I have learnt from this little 'adventure' is that it is worth the few seconds it takes to chmod your media files to read only.  That way unless you are root you will never have to worry about deleting them.  

Sorry about the long post, but I hope it might prevent someone from making the mistakes I did.

---

