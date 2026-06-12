---
title: "Boot screen hanged up! - fsck"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by mcglnx on 2006-12-19
Dear All,

Edgy's new boot screen is nice, however, there is something **[COLOR="DarkRed"]very annoying[/COLOR]** 

Whenver fsck starts at boot time, the boot screen (which I like) locks, hangs up until the end of fsck process.

I do not think this is very user friendly - I was even surprised, rebooted twice then finally on 'rescue mode' to realize it was due to fsck.

I'd suggest to have at least amessage explaining what's happening for those 'specifics' situations.

Thanks,
M.

---

### Post by bulldog on 2006-12-19
Well if fsck starts I see a black screen which informs me what is happening and how far it is with checking the file system.

That is the normal procedure I presume.
Why it's not working on your computer beats me,but it's not the normal way fsck is doing it's thing.

---

### Post by mcglnx on 2006-12-19
No, I do not see anything! May be it is related to my "Scrambled" console screens on my Inspirong 6400?? :(

---

### Post by bulldog on 2006-12-19
Could be,hard to tell from here :D 
But if you know what's happening what's the big deal.
I know you would have it fixed,but I really have no clue about it,sorry.

---

### Post by mcglnx on 2006-12-19
The fact is that YOU told me something is written on the screen - which is not what I've seen. 
Then I started to suspect the 'scrambled screen' issue.

Thanks anyhow for your suggestion.
Cheers

---

### Post by louieb on 2006-12-20
I have a machine that I play with and if I change the file system on a partition that is listed in the /ect/fstab file.
On reboot it will give me nasty messages and boots to the single user command line.
In my case to fix it, I use ```
nano  /etc/fstab 
```and correct  the file type for that partition.

---

### Post by mcglnx on 2006-12-20
Hmm, thanks for the hint, but it has nothing to do with a bad partition.
It is a normal fsck happening every 30 (? correct me if I'm wrong) reboots.

---

### Post by confused57 on 2006-12-20
> **mcglnx said:**
> Hmm, thanks for the hint, but it has nothing to do with a bad partition.
It is a normal fsck happening every 30 (? correct me if I'm wrong) reboots.

I had a problem recently with Edgy not showing it was doing a fsck check, but my HDD activity light was constantly on so I assumed that's what was happening...it's only occurred that one time, but it appeared that my pc had locked up.  I've always had a progress indicator before when a fsck was taking place on a partition...I just let it complete the process, without seeing what partition was being fsck'd or the progress.

---

### Post by syracus on 2006-12-30
Hi all,

i recently (well, even tonight) i ran into the '30th mount -> fsck' boot hang error also :( I can't really see where's the problem. Doing a boot into recovery mode and issuing a '> fsck -As' manually seems to fix the problem.

My fstab looks like 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=db71abf8-a2b6-4052-8523-83d145287de7 /               ext3    defaults,errors=remount-ro 0       1
#### UUID=db71abf8-a2b6-4052-8523-83d145287de7 /               ext3    defaults,errors=remount-ro 0       0
# /dev/hda1
##UUID=3bbb0410-2a2d-42fd-96f9-11e95d47792f none            swap    sw              0       0
UUID=2453228e-9f7e-46f6-9ba9-16e181eeaa5b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is based on the default installation procedure.

As i love ubuntu so far very much (and well have tried almost any distribution out there ;) ) i would love to here, that this is a know bug which will be fixed in a comming-up release.

Other hints to work-around the problem 'till then would also be very nice to hear.

greets 2@ll

---

