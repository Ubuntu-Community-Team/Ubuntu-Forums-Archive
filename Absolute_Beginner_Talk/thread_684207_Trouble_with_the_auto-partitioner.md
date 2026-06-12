---
title: "Trouble with the auto-partitioner"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-01-31
Ok, so I posted earlier with a problem where I didn't have the option for guided- resize install. It was suggested that my drive was full, however I just double checked and it's definitely not: 

[IMG]http://img206.imageshack.us/img206/3589/31994173rx7.jpg[/IMG]

Any idea why that option would be missing? Do I have to do something to switch part of that to ext3 ahead of time so Ubuntu can live there?

I'd like to install ubuntu and have about 5-10 gigs of extra space for stuff Ubuntu can use. I figure if I give it 20 gigs that should be plenty. 

Here's what the manual option looks like, showing also that there's a good amount of unused space on sda2, which is C. 

[IMG]http://img134.imageshack.us/img134/5320/manualgq3.png[/IMG]

---

### Post by oedha on 2008-01-31
funny.....you have free space at the beginning....that's fine.....
means that you windows was the /dev/sda2 ntfs.......be carefull with this....
i see that you only have around 3Gb........
i suggest you to get Gparted....and resize the ntfs......
make the 3Gb to 7 or 8 Gb.........
and dont forget...swap = twice of your RAM size

~E~

---

### Post by dgbearcat on 2008-01-31
> **oedha said:**
> funny.....you have free space at the beginning....that's fine.....
means that you windows was the /dev/sda2 ntfs.......be carefull with this....
i see that you only have around 3Gb........
i suggest you to get Gparted....and resize the ntfs......
make the 3Gb to 7 or 8 Gb.........
and dont forget...swap = twice of your RAM size

~E~


So I guess that 3gig section at the end is the swap? I've got 2 gigs of ram, so I can expand that further. 

Is Gparted something to take the NTFS that takes up the whole drive and size that down so that there's "unformated" section for Ubuntu?

---

### Post by Rocket2DMn on 2008-01-31
Before you resize the drive, it needs to be defragmented (some people suggest you defrag it twice).  This will move data to the front of the drive and clean out space at the end where you can shrink the partition and use that space for something else (like Ubuntu).

---

### Post by Moop on 2008-01-31
You can use the partition editor on the live cd to resize your partition. It's found in System-Administration. You shouldn't need to create a ext3 partition before you install. After you have free space you should be able to choose "use largest continuous free space" during the install.

---

### Post by dgbearcat on 2008-01-31
> **Rocket2DMn said:**
> Before you resize the drive, it needs to be defragmented (some people suggest you defrag it twice).  This will move data to the front of the drive and clean out space at the end where you can shrink the partition and use that space for something else (like Ubuntu).

I defragged just a bit before I tried, but another run through wouldn't hurt I'm sure. Thanks!

---

### Post by dgbearcat on 2008-01-31
> **Moop said:**
> You can use the partition editor on the live cd to resize your partition. It's found in System-Administration. You shouldn't need to create a ext3 partition before you install. After you have free space you should be able to choose "use largest continuous free space" during the install.

I'll try this, as I hadn't seen it before. If I just section of a 20 gig partition, can I then tell it to do a "full disk install" there and it will act like a completely separate drive? 

Heh, I hate feeling like a complete computer-moron, but I guess this just isn't something I play with often enough to know :)

---

### Post by Moop on 2008-01-31
> **dgbearcat said:**
> So I guess that 3gig section at the end is the swap? I've got 2 gigs of ram, so I can expand that further. 

Is Gparted something to take the NTFS that takes up the whole drive and size that down so that there's "unformated" section for Ubuntu?

The 3gb partition isn't swap. If you have 2gigs of ram then you don't need much swap. 1.5gb would be plenty.

---

### Post by Rocket2DMn on 2008-01-31
Also, PLEASE PLEASE make sure you have everything important backed up before you proceed.  Although there shouldn't be any problems, if something *does* go wrong (bad resize, power outage, who knows what), it is always good to keep complete and up to date backups.
Good luck, and post back if you have other questions, concerns, or problems!  Welcome to Ubuntu!

PS: As per Moop's suggestion, have your swap at least match your RAM.  Though you may not use it as true swap, this is where the contents of RAM is written when you hibernate the computer, so it should be at least the size of your RAM.

---

### Post by dgbearcat on 2008-01-31
> **Rocket2DMn said:**
> Also, PLEASE PLEASE make sure you have everything important backed up before you proceed.  Although there shouldn't be any problems, if something *does* go wrong (bad resize, power outage, who knows what), it is always good to keep complete and up to date backups.
Good luck, and post back if you have other questions, concerns, or problems!  Welcome to Ubuntu!

PS: As per Moop's suggestion, have your swap at least match your RAM.  Though you may not use it as true swap, this is where the contents of RAM is written when you hibernate the computer, so it should be at least the size of your RAM.

Oh, I've got a 160 gig external HD that I have everything backed up on, so that's not a worry. 

If that 3 gigs isn't swap, and my cd drive had a regular (700 mb) cd in it, any idea what those two sections of other space are?

Also, before I do take the plunge, and having to reinstall XP quite a few times for a number of reasons: any advice on creating/exporting some kind of "driver profile" so that next time I don't have to go out and find all of them?

---

### Post by Moop on 2008-01-31
I would guess those other 2 partitions are for system restore or something like that. Some hard drives have hidden partitions for restoring your system to factory condition. But it's just a guess. Try taking a look at them with the live cd.

---

### Post by dgbearcat on 2008-02-01
> **Moop said:**
> I would guess those other 2 partitions are for system restore or something like that. Some hard drives have hidden partitions for restoring your system to factory condition. But it's just a guess. Try taking a look at them with the live cd.

That's what they looked like, so I just left them alone. I used Gparted to scale down my NTFS section to about 65 gigs, leaving a good 20 for Ubuntu. Even so, when I try installing, it STILL doesn't seem to want to do the auto scaling thing, although now it gives me the option to do it on my external HD which wasn't plugged in last time. 

I think I'll try the manual option, because I'm pretty sure the new sda created from the new partition is visible there, so maybe it'll let me pick it. 

Thanks for all the help, and I'll probably be back for more!

---

### Post by dgbearcat on 2008-02-01
Ok, sorta new problem, possibly not. Also, I found out that the 1 and 3 partitions are "dell restore" and "dell utility" so I'm going to be leaving those alone. 

Ok, so I used Gparted to make things look like this: 

[IMG]http://img216.imageshack.us/img216/4299/gpartedid1.png[/IMG]

Fine and dandy. Now, when I try to use the install, it gives me three options: 

[IMG]http://img46.imageshack.us/img46/953/guidedyg2.png[/IMG]

Now, I would at least assume that using the "largest continuous space" would mean the 20something gigs there, and selecting that option gives me this just before install: 

[IMG]http://img502.imageshack.us/img502/8462/readytoinstallcf6.png[/IMG]

Now, it tells me that partitions five and six are going to be formated into ext3 and swap. My concern is that I can't tell from anywhere specifically what those partitions are. I'm assuming that partition 5 is that 20 gig space, but what is 6? I don't want to accidentally overwrite any of my windows backups or whatever it puts there. Also, shouldn't it be saying that it's putting it on 4 and 5? There are only 3 official partitions in gparted from what I can see. 

So I try doing it in "manual" mode, which shows this: 

[IMG]http://img142.imageshack.us/img142/5327/manualjm0.png[/IMG]

Clicking  on the "free space" segment lets me make a partition of it to use as swap, so I do so, and then make the rest ext3, giving me the following screen:

[IMG]http://img513.imageshack.us/img513/149/newmanualmk3.png[/IMG]

Now, this looks like it should be fine and ready. However, trying to continue gives me this: 

[IMG]http://img526.imageshack.us/img526/8905/windowswarningrg6.png[/IMG]

which, when ignoring of will give me this: 

[IMG]http://img526.imageshack.us/img526/315/newerrordi7.png[/IMG]

So, I suppose my questions are two: 

1. Since the manual setup ended up giving me sda5 and sda6 as my ext3 and swap, would just using the automatic thing probably be fine?

2. If you're not totally sure that the above wouldn't mess with my windows install, do you have any idea how to set it up manually so that I'm not getting those errors? Or, alternatively, how bad would it be to bypass the errors and continue anyway?

Thanks a ton for all the help already, and for all of it forthcoming.

---

### Post by Moop on 2008-02-01
You can just ignore that fat16 partition. You should use the "guided use the largest continuous free space" and NOT the "use entire disk" option. 

Everything else looks ok. You can't see the partitions before they are created but Partition 4 would be a extended partition that goes contains your swap and partition 5 would be your / partition. Partition 6 is your swap. A standard Ubuntu install will create 2 partitions for swap. A extended partition and the swap. It all looks normal.

---

### Post by dgbearcat on 2008-02-01
> **Moop said:**
> You can just ignore that fat16 partition. You should use the "guided use the largest continuous free space" and NOT the "use entire disk" option. 

Everything else looks ok. You can't see the partitions before they are created but Partition 4 would be a extended partition that goes contains your swap and partition 5 would be your / partition. Partition 6 is your swap. A standard Ubuntu install will create 2 partitions for swap. A extended partition and the swap. It all looks normal.

Cool beans, I'll be trying this out later this afternoon. Hopefully I'll be able to respond from inside Ubuntu without the CD!

---

