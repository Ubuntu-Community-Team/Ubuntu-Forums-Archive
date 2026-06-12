---
title: "Partition problem"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Gritz on 2007-01-14
After installing Ubuntu on a second hard drive (a small 3.2 GB Fijutsu) it became apparent that I would need more space so I purchased an 80 GB HD and cloned Ubuntu over to it, and then removed the small Fujitsu. I now had a dual boot system .... XP on the 1st hard drive and Ubuntu on the 2nd. However .... looking at my new hard drive specs, it appears that the same size limitations are still in place , that is, the active boot partition is still the same 3.2 GB that it originally was. My belief is that if I don't enlarge this partition I will be heading for a system crash when I run out of space as system upgrades and software installs keep filing up the empty space on the boot partition.

I booted the Gpart Live CD and attempted to resize and it appears that I can change the Swap (hdb5) and the Extra Space (hdb3) but not the boot (hdb2). Is it possible to copy the boot partition to the large partition and move the swap file or fix it in a similar manner?  It appears that there is data on hdb3 so I'm unsure if I can copy over to it without destroying the data.

I just want to enlarge the boot partition if possible and not have to reinstall .... since it all works at the moment. :confused:

---

### Post by Buck2348 on 2007-01-14
Please post the output from
```
df -h
```
It appears to me that hdb2 is an extended partition and therefore not the Linux boot partition.

Buck

---

### Post by mdsmedia on 2007-01-14
> **Buck2348 said:**
> Please post the output from
```
df -h
```
It appears to me that hdb2 is an extended partition and therefore not the Linux boot partition.

BuckThat's the way it looks to me too, and if the extended partition (hdb2) is within the boot partition (hdb1), if I'm not mistaken that might be why you can't resize hdb2....it's already as large as the partition in which it resides (hdb1).

---

### Post by Buck2348 on 2007-01-14
I think hdb5 and hdb**-**1 (note the hyphen) are inside the extended (hdb2) partition.  I think you're correct that the system (root) is on hdb1 and if so it does need to be enlarged a bit.

Buck

---

### Post by rccharles on 2007-01-15
> **Gritz said:**
> 

I booted the Gpart Live CD and attempted to resize and it appears that I can change the Swap (hdb5) and the Extra Space (hdb3) but not the boot (hdb2). Is it possible to copy the boot partition to the large partition and move the swap file or fix it in a similar manner?  It appears that there is data on hdb3 so I'm unsure if I can copy over to it without destroying the data.

I just want to enlarge the boot partition if possible and not have to reinstall .... since it all works at the moment. :confused:

Have you tried making the extended partition larger?

...

What you could do is put your smaller drive back in your machine.  Re-partition the smaller drive so that it is all one big ext3 partition. Do a backup of the boot partition then restore the partition.

Here is some help on using tar for backup:

[http://db.assam-glug.org/documentations/Linux-admin-made-easy/server-backup.html](http://db.assam-glug.org/documentations/Linux-admin-made-easy/server-backup.html)

see the section 8.1.1. Backing up with ``tar'':

Robert

---

### Post by old_geekster on 2007-01-15
> **Gritz said:**
> After installing Ubuntu on a second hard drive (a small 3.2 GB Fijutsu) it became apparent that I would need more space so I purchased an 80 GB HD and cloned Ubuntu over to it, and then removed the small Fujitsu. I now had a dual boot system .... XP on the 1st hard drive and Ubuntu on the 2nd. However .... looking at my new hard drive specs, it appears that the same size limitations are still in place , that is, the active boot partition is still the same 3.2 GB that it originally was. My belief is that if I don't enlarge this partition I will be heading for a system crash when I run out of space as system upgrades and software installs keep filing up the empty space on the boot partition.

I booted the Gpart Live CD and attempted to resize and it appears that I can change the Swap (hdb5) and the Extra Space (hdb3) but not the boot (hdb2). Is it possible to copy the boot partition to the large partition and move the swap file or fix it in a similar manner?  It appears that there is data on hdb3 so I'm unsure if I can copy over to it without destroying the data.

I just want to enlarge the boot partition if possible and not have to reinstall .... since it all works at the moment. :confused:
You didn't mention which version of Ubuntu that you installed, but I also have an 80GB HDD w/Ubuntu 6.10.  I made three partitions: / 10GB,  swap 3GB and /home 64GB.  This gave me plenty of room for each.

I would suggest that you do a complete install, since you probably don't have allot of data to lose at this point.  A fresh install will eliminate your problems.

---

### Post by Gritz on 2007-01-15
> **Buck2348 said:**
> Please post the output from
```
df -h
```
It appears to me that hdb2 is an extended partition and therefore not the Linux boot partition.

Buck

Attached.  When I first installed Ubuntu 6.06 I had a 3.2 GB HD .... no partitions, clean, formatted.  Ubuntu created whatever partitions and swap space it wanted. When I cloned to an 80 GB I got the same thing in just a portion of what was available  ... I DID enlarge the Swap Space to about 512 MB, and I THINK I initialized the largest leftover space and formated it (but it's hard to tell if it's useable because when I click on "Enable" it does nothing ... so perhaps it's not even being used. However, I DO see part of it taken up with data .... whose data I don't know. Maybe overhead .... or maybe my apps.  Additionally ... I see about 5 GB of space adjacent to the swap (in the graphic anyway) that isn't even being listed. 

I'd rather not start over since it's all working so well .... my graphics drivers work well, Google Earth is installed, and my VIDEO and mp3 finallllllly work. So ..... if new updates and new installs will not impact the Active/Root .... I would think I'm ok??  Well .... I'm probably just being hopefull.  ](*,)

---

### Post by Buck2348 on 2007-01-15
I'm a little hesitant to try to instruct you on this since I've not got much experience myself.  But this should do no harm, anyway:
```
sudo mkdir /media/hdb3
sudo mount /dev/hdb3 /media/hdb3
```
That should allow you to look in the new folder /media/hdb3 and see what is on that partition.
When you were looking at the disk with Gparted, did you try to enlarge the hdb1 partition?  That is definitely your root partition, and as far as I can see the only partition that Ubuntu is using.  I think you're right that it needs to be enlarged.  I'm going to do a little googling now to see if I can find out if this can be done.

Buck

---

### Post by Buck2348 on 2007-01-15
As far as I can see, you ought to be able to do what you like with the partitions using GParted on a live CD.  What you have now is:  / (root, boot, system--all of Ubuntu except the swap partition) on hdb1, swap on hdb5, free space labeled /dev/hdb-1 (note the hyphen), an extended partition on hdb2, which contains hdb5 and /dev/hdb-1, and the big one hdb3.  The function of an extended partition is only to contain other logical partitions and get around the limit of four primary partitions on a disk.  I don't know why you have an extended partition there--it is not of much use.

Anyway, you ought to be able to move the beginning of hdb3 in (to the right), move hdb2 to the right, and then grow hdb1 to any size you like.  I think I would consider deleting the extended partition hdb2 since it's not really being used--that will free up the 4.49 GB labeled as /dev/hdb-1, in which case you could choose to leave hdb3 alone.

Hope this helps.  I'd be interested to hear if you solve the problem.

Buck

---

### Post by Gritz on 2007-01-15
> **Buck2348 said:**
> As far as I can see, you ought to be able to do what you like with the partitions using GParted on a live CD.  What you have now is:  / (root, boot, system--all of Ubuntu except the swap partition) on hdb1, swap on hdb5, free space labeled /dev/hdb-1 (note the hyphen), an extended partition on hdb2, which contains hdb5 and /dev/hdb-1, and the big one hdb3.  The function of an extended partition is only to contain other logical partitions and get around the limit of four primary partitions on a disk.  I don't know why you have an extended partition there--it is not of much use.

Anyway, you ought to be able to move the beginning of hdb3 in (to the right), move hdb2 to the right, and then grow hdb1 to any size you like.  I think I would consider deleting the extended partition hdb2 since it's not really being used--that will free up the 4.49 GB labeled as /dev/hdb-1, in which case you could choose to leave hdb3 alone.

Hope this helps.  I'd be interested to hear if you solve the problem.

Buck

Buck, thanks for the encouragement and advice.  I took a deep breath and decided to make a stab at it. Remember though ... this was a partition layout that I did not create, and it was cloned over exactly as it was .... (still too small). Anyway ... it appears it can be done at this point ... but is it stable?  I'm not sure.  Here's how it went.

1. I resized the largest partition on the left side to half it's original size.
2. I deleted the "unallocated" space within the Extended partition that was not being used.
3. I deleted the Swap partition.
4. I resized the primary partition to the right leaving a 512 MB gap between the two.
5. I created a Swap partition in the 512 MB gap.

So ...  to check I ran dh -f  (which seems to tell me only about the Primary Partition)
So to check more .... from a Terminal I ran .... sudo qtparted and came up with "Bad device, invalid or uninitialized input device 166" (Twice with the same error lines). Possibly it is trying to read my first drive hda1, which is NTFS, bit I don't know.

Now I have no idea what that is all about .... but running qtparted gave me errors even BEFORE I made the changes so I'm ignoring that. Oddly enough right after the error lines, qtparted v0.4.5-cvs comes up correctly (I think) in a separate window giving a graphical picture of my NEW hard drive. (Picture attached).

So at this point ..... success!  :mrgreen: :D :mrgreen:

---

### Post by Buck2348 on 2007-01-15
Well, good!  That looks good to me--you certainly have enough size in the root partition now.  Yes, the df command gives info only on mounted filesystems, that is that you can access with system commands or in the GUI.  Mounting is normally done during boot in accordance with the contents of the /etc/fstab file.  If you want to look into your third partition to see what is there, ```
sudo mkdir /media/hdb3
sudo mount /dev/hdb3 /media/hdb3
```
should allow you to do that.  Just click Places -> File System -> media -> hdb3.  There seems to be less stuff there than earlier.

You might at some point want to make a separate partition for your /home directory.  That is where by default all the settings for your system and apps, and all your data files are placed.  It's a little like Windows' My Documents but much more useful, being on a separate partition.  Then if it should become necessary you can reinstall your system without losing any of your data files or settings.  You have plenty of room now just to shrink hdb1 back to 8 or 10 gig and put /home right after it.  If you put a lot of music and pictures in there and start to fill that home partition, you could mount the third partition as a subdirectory of /home and again have lots of room.

Cheers,
Buck

---

### Post by Gritz on 2007-01-15
Thanks Buck,
   I appreciate your help and suggestions (which I printed out).  All excellent points, and I'll implement them as I learn more!  8) 8) 

Take Care,

Gritz

---

### Post by Gritz on 2007-01-16
> **Buck2348 said:**
>  If you want to look into your third partition to see what is there, ```
sudo mkdir /media/hdb3
sudo mount /dev/hdb3 /media/hdb3
```
should allow you to do that.  Just click Places -> File System -> media -> hdb3.  There seems to be less stuff there than earlier.

You might at some point want to make a separate partition for your /home directory.  That is where by default all the settings for your system and apps, and all your data files are placed.   You have plenty of room now just to shrink hdb1 back to 8 or 10 gig and put /home right after it.  If you put a lot of music and pictures in there and start to fill that home partition, you could mount the third partition as a subdirectory of /home and again have lots of room.

Cheers,
Buck

Buck ..... Ok, it does look like less space in hdb3. I see cdrom, cdrom0 & lost+found. Nothing in the first 2, and can't access lost+found ... (permission denied). 

If you can continue my lesson ...  :mrgreen:  say I do create a separate partition for /home how am I  going to point /home to this new partition?  I can easily create the partition .... but configuring it to be /home I don't understand .... and .... does it need to be mounted at boot time? Hope I'm not taking up too much of your time ..... :-k :mrgreen:

---

### Post by bodhi.zazen on 2007-01-16
I have not read the whole thread, but here is how to move home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Gritz on 2007-01-16
Thanks Bodhi,
    I am in the process of either fixing it, or crashing it right now. I appreciate the help and will post my success or failure.  :KS

---

### Post by Gritz on 2007-01-16
> **bodhi.zazen said:**
> I have not read the whole thread, but here is how to move home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

One of the commands on the one of the links didn't seem to work and it appeared to be a typo.  The command on one of the sites was:

 #  find . -depth -print0 | cpio -null -sparse -pvd /mnt/newhome/

What DID work was:

 #  find . -depth -print0 | cpio *--null --sparse* -pvd /mnt/newhome/  (2 hypens in stead of one!)

Anyway ..... it SEEMS to be working ok. Thank you for the links! :mrgreen: 

One question?  I created a new swap file .... do I need to make it Active or something?
It doesn't seem to be using any space at all.

I Appreciate all the help .......  :D :D

---

### Post by bodhi.zazen on 2007-01-16
Depending on how much RAM you have you may not use swap much ....

What do you get when you type ```
free
``` in a terminal ?

You should see information on swap (how large it is and how much you are using)

If not, post output of free, you partition for swap (hda?), and the line for swap in fstab (/etc/fstab)

Oh that  - - doubble hyphen, some browsers/wiki sites render a - - as a single - :(

---

### Post by Gritz on 2007-01-17
> **bodhi.zazen said:**
> Depending on how much RAM you have you may not use swap much ....

What do you get when you type ```
free
``` in a terminal ?

You should see information on swap (how large it is and how much you are using)

If not, post output of free, you partition for swap (hda?), and the line for swap in fstab (/etc/fstab)



Ok .....  here's the output.  I have 256 MB Ram .... probably borderline for XP but maybe ok for linux?  I don't SEE any performance loss .... but I just want to make sure I've set it up right!

---

### Post by bodhi.zazen on 2007-01-17
Looks OK to me :p

What is the output of the free command in a terminal, that tells me a little more :D

---

### Post by Gritz on 2007-01-17
> **bodhi.zazen said:**
> Looks OK to me :p

What is the output of the free command in a terminal, that tells me a little more :D

Ummm .... My 1st attachment was in a Terminal.  I just did it again .... just 3 lines (Memory, Buffer, & Swap) Only this time it showed some useage in Swap (62,456) so maybe it IS working!  

Seems ok ....  If everyone had the same experience as I have with Ubuntu (although it's taken some effort on my part) I can't see how Vista would ever get off the ground!  The reason I'm delving into Ubuntu is that I can't see paying that kind of money for an OS! I'm betting the public at large won't pay for it ... and most likely only get it with a new system.  We'll see.

Thanks again for your efforts. :) :)

---

### Post by bodhi.zazen on 2007-01-17
That tiny thing is a terminal ???

OK lets look ....

Oh I see it now, don't know how I missed that one :p

Yes, you swap is fine :p

But you already know that ;)

---

### Post by Gritz on 2007-01-17
Bodhi,
  Great ..... thanks for looking.  My mind can go on to other things now. :mrgreen: :mrgreen:

---

