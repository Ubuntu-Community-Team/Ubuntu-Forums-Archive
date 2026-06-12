---
title: "complete newbie help with drive access"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by karan733 on 2006-08-17
hello all,

Id like to apologise for making my first post here a question, but i intend to stick around for a while :) (hopefully!)

I am having a problem with doing certain tasks in ubuntu, and im sure these are due to my inabilities (why else does linux ever fail?!), but im unable to spot them. 

I have two HDDS, called Primary (C:) with 120GBs and Secondary (Z:) with 160GBs. After trying for a whole day to partition primary, I found GParted wouldnt work because there were bad sectors on the drive. So I partitioned the newer secondary drive, and successfully installed ubuntu - or so I thought!

So now I have primary C: with Windows XP SP2 installed, and secondary Z: with ubuntu Dapper installed. But when i log into ubuntu, I am unable to run or open any files, or any type on either the secondary or primary HDDS! I cannot even paste items into either drive from my home directory. 

Can someone spot what I have done wrong, or how I can fix this problem please? :(

Also, I cant seem to run .exe files in ubuntu. As a complete newbie to linux, is it possible to run windows exe's on linux, or am i just being plain stupid?

Thanks in advance!
karan733

---

### Post by karan733 on 2006-08-17
I guess I should say the following things too. 

hda  is NTFS, one partition AFAIK
hdb1 is NTFS, one partition size x-19GBs (ie, I cant remember :D )
hdb2 is linux-swap, 3 GBs
hdb3 is ext3 (ubuntu 6.06), 16GBs

Thanks again

---

### Post by dillbertdabomb on 2006-08-17
1. ntfs filesytems are hard to mount in linux. I found that out 
[here]("http://www.ubuntuforums.org/showthread.php?t=237821")

2. linux is not windows, you can't run exes, linux does have its limitations as you will soon find out...

---

### Post by karan733 on 2006-08-17
cheers dillbert,

only one problem though. I think i messed up when doing my partitions. I followed this step...

> **bodhi.zazen said:**
> Open a terminal.
At the CLI type:
sudo nano /etc/fstab

Use arrow keys, change the portion of the line 
/dev/hda2 ............... auto,ro   0  0
to read:
/dev/hda2 ............... users,rw (likely reads auto,ro)
Leave the 0 0
?May be /dev/hda1 rather then /dev/hda2
the mount point is listed in the second comlumn

When finished type Ctrl X, type y for save.

change ownership of you mount point as above.

Unmount and then re-mount the drive.

umount /mnt/mount_point (NOTE: NOT unmount, just 1 u)
mount /mnt/mount_point

In Ubuntu mount pint may be may be /media/windows ?
Sorry, I am rusty with Windows.

Your changes will not be saved when you re-boot.



however, when i do the above (the sudo nana /etc/fstab bit) I get the following output, and no mention of auto, ro 0 0 :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc             /proc           proc    defaults        0       0
/dev/hdb3        /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1        /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1        /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb2        none            swap    sw              0       0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto     0       0


```

and as such, I dont know where to edit the r/w access :(  there is one at /dev/hdb3 (which is my / partition) but im not sure how that would affect the r/w access to hda1 and hdb1 :confused: 

any ideas?

thanks again
karan

---

### Post by blackened on 2006-08-17
Are you able to create files in your home directory? If so, then you may just be misunderstanding the filesystem:

Regular users are only allowed to create/edit files in their home directory. All other files require superuser privileges to discourage accidental mishaps. 

For the primary drive (WinXP) try reading this thread:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g")

---

### Post by karan733 on 2006-08-17
> **blackened said:**
> Are you able to create files in your home directory? If so, then you may just be misunderstanding the filesystem:

Regular users are only allowed to create/edit files in their home directory. All other files require superuser privileges to discourage accidental mishaps. 

For the primary drive (WinXP) try reading this thread:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g")
hmmm, I can create a new folder called untitled in my home dir, and then delete it. I can also move a file or folder from C: or Z: to my home dir, and then delete it. But I cannot move a file from my home dir to the C: or Z: NTFS partitions.

just gonna go off and read the link you posted :)

---

### Post by blackened on 2006-08-17
That's wierd. Didn't you say that hda was WinXP and hdb was Ubuntu?

Why is hdb1 mounting as ntfs?

Either way, ntfs mounts read-only by default in Ubuntu. So the ntfs-3g driver should help you.

---

### Post by karan733 on 2006-08-17
> **blackened said:**
> That's wierd. Didn't you say that hda was WinXP and hdb was Ubuntu?

Why is hdb1 mounting as ntfs?

Either way, ntfs mounts read-only by default in Ubuntu. So the ntfs-3g driver should help you.
hdba is full NTFS (only one partition) 

the hdb is split into three parts. 

hdb1: data file store, no OS as such, but formatted to ntfs. 
hdb2: swap file, linux-swap
hdb3: ubuntu ext3

hope this clears things up, sorry i dont really know what im talking about, just trying to learn as i go along! 

thanks for the help :)
karan

---

### Post by syedn on 2006-08-17
As you said in your last post, you are correct you shouldn't be able to move anything from your /home/USER$ directory to the NTFS partitions because Linux cannot natively write to NTFS (though there are ways around this).


also you might try running wine (winehq.com) to see if you can get your EXEs running favorably under Ubuntu :)

---

### Post by blackened on 2006-08-17
No reason to be sorry, we all have to start somewhere.
The more you ask and read, the more you learn, the less you have to ask and read. :)

I've had good results with the 3g driver for reading/writing ntfs. And wine works exceptionally well for me on most things Windows.

---

### Post by karan733 on 2006-08-17
> **syedn said:**
> As you said in your last post, you are correct you shouldn't be able to move anything from your /home/USER$ directory to the NTFS partitions because Linux cannot natively write to NTFS (though there are ways around this).


also you might try running wine (winehq.com) to see if you can get your EXEs running favorably under Ubuntu :)

Fantastic! it works :D I can move files to and from the two ntfs partitions :D

to any other new users reading this thread for information:

1) Read the above posts
2) Read [this]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g") thread - it takes you through the process step by step, and in my case got it working first time (I hope it keeps working!)


Good luck!


Thank you all for helping out :) absolutely fantastic support! :)

karan

---

### Post by blackened on 2006-08-17
Cool. Glad you got it working. :)

---

