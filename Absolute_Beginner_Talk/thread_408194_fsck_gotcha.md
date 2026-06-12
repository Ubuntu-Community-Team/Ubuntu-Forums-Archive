---
title: "fsck gotcha ?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by mspendlo on 2007-04-13
Well, a gotme anyway..

Not really requiring a reply to a problem as such, more opening up discussion around this issue.

I have noticed that my file system had been a little "unstable", in terms of MP3s disappearing anyway. (don't think this caused [http://ubuntuforums.org/showthread.php?t=408155]("http://ubuntuforums.org/showthread.php?t=408155"), but it might have..)

I have dual boot Ubuntu 6.10 and winXP. Outside of the main o/s partitions I have a fat32 "/data" partition that both o/s write to.

I noticed the creation of a bunch of "fsckNNN.rec" files (NNN == numeric e.g. fsck001.rec) which I had ignored until I got suspicious one day and started to read up on `fsck' and `fstab' etc.

So, turns out `fsck' had been marking my fresh MP3s as corrupt or incomplete in some way renaming them in the above format i.e. fsck001.rec. 

How do I know this ? well, if I rename to fsc001.mp3 and open in a player, the audio portion of the file still exists. They are COMPLETE mp3 tracks ??

For those that don't know, you can see what fsck has been up to in :

/var/log/fsck

Anyways, I decided I'd let winXP deal with the fat32 disk so I changed my fstab to   make Ubuntu ignore these mounts when checking the file system on boot :

sudo vi /etc/fstab   

and I edited the 6th field to "0" for the fat32 partitions. 

Any words of wisdom ? I am happy enough to let winXP check the fat32 disk but I thought fat32 from linux was no probs ?

If this happens to others then it's a BIG gotcha I'd say..

---

### Post by freebird54 on 2007-04-13
It may be a gotcha - or it may be the best that can be done with a corrupt filesystem.  Have you run scandisk (or CHKDSK /F) with force fixes lately?  You may find a few more similar things floating around (like filechk.000) from the Windows version of the process.

I would certainly be very suspicious that this is so.  personally- I use the CHKDSK with the Force option to be sure what it is doing...

Good luck!

EDIT:  BTW - good idea to leave Windows to handle it - for boot speed if nothing else.  BUT - you have to tell Windows to do it! :)

---

### Post by mspendlo on 2007-04-13
> **freebird54 said:**
> It may be a gotcha - or it may be the best that can be done with a corrupt filesystem.  Have you run scandisk (or CHKDSK /F) with force fixes lately?  You may find a few more similar things floating around (like filechk.000) from the Windows version of the process.

Yea, first thing I did was run `chkdsk' in winXP. It all seemed ok.

I guess really it should be obviously pointed out in config guides that Ubuntu shouldn't check fat32s - if indeed it is unreliable ?

---

### Post by su_penguin on 2007-04-13
My checkfs: 

Log of fsck -C -R -A -a 
Thu Apr 12 23:22:19 2007

fsck 1.39 (29-May-2006)

Thu Apr 12 23:22:19 2007
----------------


My checkroot: 

Log of fsck -C -a -t ext3 /dev/hda1 
Thu Apr 12 23:22:18 2007

fsck 1.39 (29-May-2006)
/dev/hda1: clean, 208496/1196032 files, 1731893/2391669 blocks

Thu Apr 12 23:22:18 2007
----------------


And I've been playing mp3's for a while now.

---

### Post by freebird54 on 2007-04-13
If the /F option wasn't used - it probably didn't do anything (in case you didn't know that).  other than that - I have several vfat32 partitions, and have never had an issue (other than slow bootups) with any of them being checked by Linux....

---

### Post by mspendlo on 2007-04-13
> **su_penguin said:**
> My checkfs: 

Log of fsck -C -R -A -a 
Thu Apr 12 23:22:19 2007

fsck 1.39 (29-May-2006)

Thu Apr 12 23:22:19 2007
----------------


My checkroot: 

Log of fsck -C -a -t ext3 /dev/hda1 
Thu Apr 12 23:22:18 2007

fsck 1.39 (29-May-2006)
/dev/hda1: clean, 208496/1196032 files, 1731893/2391669 blocks

Thu Apr 12 23:22:18 2007
----------------


And I've been playing mp3's for a while now.

Not sure how that's relevant ? The post is about the safety of `fsck' against fat32 partitions...

---

