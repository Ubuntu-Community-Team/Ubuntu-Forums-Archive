---
title: "creating a linux swap file"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-09-25
Ive managed to now set my partitions up as 25gb ntfs (win xp), 15gb (ubuntu) 35gb fat32 (to share files between to two os) and there is a 10mb unknown.
To manage this I needed to delete my linux swap file as gparted was complaining that there were already too many partitions.
Questions...do I need it and if so how do I make another one?
Thanks

---

### Post by xpod on 2006-09-25
Thats weird seeing as you only got three...or 4 previously
I think you can have as many as you want as long as only 4 are primary ones.

Even that might be windows im thinking about

---

### Post by xpod on 2006-09-25
:confused:

---

### Post by drifternel on 2006-09-25
woops,
not sure which bit of that link I need.
I dont want to reinstall ubuntu as its working fine now.
Is there a way of doing it without starting over again?
Thanks

---

### Post by bodhi.zazen on 2006-09-25
> **drifternel said:**
> Ive managed to now set my partitions up as 25gb ntfs (win xp), 15gb (ubuntu) 35gb fat32 (to share files between to two os) and there is a 10mb unknown.
To manage this I needed to delete my linux swap file as gparted was complaining that there were already too many partitions.
Questions...do I need it and if so how do I make another one?
Thanks

You can only have 4 primary partitions.

One primary partition can be an extended partition. An extended partition may have 4+ logical partitions (depends on BIOS).

To fix you problem you will need to re-partition. Delete your 35gb fat32 and 10mb "unknown" partitions. Now create a 45 Gb Extended partition. Within that extended partition create several logical partitions, one for swap, one FAT32 for share, or whatever you need.

Clear as mud ???  :cool:

---

### Post by bodhi.zazen on 2006-09-25
> **weapon-x said:**
> chk this [link ]("http://www.flynix.profusehost.net/viewtopic.php?t=9"):D

Errr wtf?

---

### Post by bulldog on 2006-09-25
Think so,remove the FAT32 and the swap and create an extended partition.
In the extended partition you create a new swap and a new FAT32 .

I think you have to manually alter your fstab to set your swap right and the FAT32 ofcourse.

You can see what your partitions are called with

sudo fdisk -l [as in like]

Beaten by bodhi-zazen again :D

---

### Post by bulldog on 2006-09-25
> **weapon-x said:**
> chk this [link ]("http://www.flynix.profusehost.net/viewtopic.php?t=9"):D


Kick weapon-x :D:D

---

### Post by xpod on 2006-09-25
And i thought i was mabey missing something...phew!

---

### Post by drifternel on 2006-09-25
ok
that seems to make sense. Im using gparted. Before i do anything silly, the 10mb partition isnt anything to do with my mbr is is????
No sure how you make an extended partition and no idea about fstab?
Can anyone walk me through?
Cheers

---

### Post by anaconda on 2006-09-25
You don't have to make a swap partition.. You can just as well do a swap-file to your ubuntu-partition.

just go to terminal and type:
```
sudo su
dd if=/dev/zero of=/swapfile bs=1024k count=256
mkswap /swapfile
swapon /swapfile

```
this makes a 256MB file.. if you want bigger just change the count=256 to any size you want..
Then that file is "converted" to swap (mkswap)
and finally the swapfile is taken in use.. (swapon)

Now the only remaining problem is that you would have to type 
swapon /swapfile
each time the machine boots.
to make it so that your swap-file is taken automatically to use each time your computer boots you have to add the swap-file to your /etc/fstab file.
 
edit your fstab file by writing 
sudo nano /etc/fstab
in terminal. And then yo have to add the following line to the fstab file:
```

/swapfile  none  swap  sw  0  0
```

and that is it.

You can see the amount of swap you have by: (in terminal)
free

EDIT:
There was/is a bug in dd. If you get segfault then you need to add
LANG=en in front of dd. eg:
LANG=en dd if=/dev/zero of=/swapfile ...

---

### Post by drifternel on 2006-09-25
have followed the instructions but have a feeling its gone badly wrong...see screenshot

---

### Post by Jonathan_DS on 2006-09-25
I'm just like you, new to Linux and I encountered the same problem.
They teach me to use Linux at school, so I heard from them that there's no problem if you have 1GB of RAM. That's more than enough and a swap isn't really neccessairy...
But during the Ubuntu installation, you can create partitions. The best way is to create the primary Ext3 partition for Ubuntu, and then an Extended Linux-swap partition.
This way you won't receive any error messages during partitioning.

Regards,

Jonathan

---

### Post by drifternel on 2006-09-25
ubuntu has restarted fine so I dont think Ive done any damage.
I do have 1gig of ram on a samsung x10+ so perhaps I should just leave it alone!
:-k

---

### Post by bodhi.zazen on 2006-09-25
> **anaconda said:**
> You don't have to make a swap partition.. You can just as well do a swap-file to your ubuntu-partition.

Nice how-to....

drifternel: You should be fine with the advice from Bull Dog or anaconda.

---

### Post by drifternel on 2006-09-25
Thanks bodhi.zazen
the advice seems fine, just not sure im doing it right, it comes up as a segmentation fault after
sudo su
dd if=/dev/zero of=/swapfile bs=1024k count=256
mkswap /swapfile
swapon /swapfile

ie. rob@rob-laptop:~$ sudo su
Password:
root@rob-laptop:/home/rob# dd if=/dev/zero of=/swapfile bs=1024k count=256
256+0 records in
256+0 records out
Segmentation fault
root@rob-laptop:/home/rob#
where am i going wrong?
Thanks

---

### Post by drifternel on 2006-09-25
one more question, how do i actually save a file onto the fat 32 partition, i cant find it when i go to save as?
Cheers

---

### Post by bulldog on 2006-09-25
> **drifternel said:**
> one more question, how do i actually save a file onto the fat 32 partition, i cant find it when i go to save as?
Cheers

I really don't know :D

I save it always in my /home and copy or move it from there to my USB hdd [extern] from time to time.

I never tried to save it there,will give it a try though if I have a moment to spare.

---

### Post by drifternel on 2006-09-25
thanks, appreciated bulldog.

---

### Post by bodhi.zazen on 2006-09-25
> **drifternel said:**
> one more question, how do i actually save a file onto the fat 32 partition, i cant find it when i go to save as?
Cheers

You have to mount the FAT32 partition read-write.

Easiest is to add a line in fstab. This is more an art then science, but this would work:
```
<dev> <mount_point> vfat auto,users,rw 0 0
```

You first make a mount point:
```
sudo mkdir /mnt/FAT32
```
Call it what you will.

If you mount it in /media rather then /mnt it will appear on your desktop (which I hate, thus the art).

If you need further help, PM **Bulldog** :p :lol:

---

### Post by raul_ on 2006-10-07
Segmentation fault here too

---

### Post by Delkster on 2006-10-07
I haven't made a swap file (I have a separate swap partition) but the last time I used dd for other purposes I also got a segmentation fault at the end. Looks like it happened only after the actual job, though, so at that time I didn't worry much.

I wonder if it's a common bug.

---

### Post by anaconda on 2006-12-29
Yep.. it actually is/was a bug in dd
the workaround was/is:

LANG=en dd if=/dev/zero of=/swapfile bs=1024k count=256

eg. to add LANG=en in front of the dd command. (shouldn't be needed)

[http://www.ubuntuforums.org/showthread.php?t=168465&highlight=lang+dd+segfault](http://www.ubuntuforums.org/showthread.php?t=168465&highlight=lang+dd+segfault)

---

### Post by theDaveTheRave on 2007-05-31
I do like the procedre that you guys are all suggesting with the swap file.

I am finding that the "default" swap  was too small and I now have problems of running out of memory, and i think it is causing me a few other various freeze ups and stuff also,

Well I actually happen to have 2 HDD in my pc, the primary is nearly full up! and the secondary has loads of space on it.

How do I use the code

<<dd if=/dev/zero of=/swapfile bs=1024k count=1024>>

so as it adds the sway file into a separate partition (eg set a 1 GB partition at the back of my second HDD and then use that??

Would I be correct in guessing it would be similar to changing <zero> for the mount number of the partition (in this case it will be seven (i think!), hence the code of

<<dd if=/dev/seven of=/swapfile bs=1024k count=1024>>

In fact i may try it anyway and see what happens!

Dave

---

### Post by bodhi.zazen on 2007-05-31
> **theDaveTheRave said:**
> I do like the procedre that you guys are all suggesting with the swap file.

I am finding that the "default" swap  was too small and I now have problems of running out of memory, and i think it is causing me a few other various freeze ups and stuff also,

Well I actually happen to have 2 HDD in my pc, the primary is nearly full up! and the secondary has loads of space on it.

LOL

Make a swap partition on the spare hd.

Mount it as your new swap.

give you old swap back to your near full disk.

---

### Post by theDaveTheRave on 2007-05-31
Nope, doesn't work....:?

:idea:  I wonder if I need to be in the correct directory?

I'll just see..... no, I think I must have to have the file in there allready.... I'll try again another time.

Dave

---

### Post by theDaveTheRave on 2007-05-31
I hate to say this but.


> **bodhi.zazen said:**
> LOL

Make a swap partition on the spare hd.

Mount it as your new swap.

give you old swap back to your near full disk.

allthought this seems like the obvious solution when I tried this GParted kept throwing some strange error message (I can't remember it right now), Even when I unmounted the original swap partition, the new partition that I had created was not being recognised!

But otherwise thanks for the help.

Truth is that this PC is rapidly coming in line for being used as a local server / files sharing / firewall / etc once I have the money for a new pc!

Which the way things are going isn't going to happen any time soon! :-({|=


Thanks again for the help guys, it is always interesting reading these forums.

Dave

---

### Post by mnml on 2007-10-16
I Am using a swapfile for my swapspace but as I have quite a lot of ram this swapfile is only used when i want to hibernate my computer. Is there anyway I can have a extendable swapfile?
so I can save some space.

---

