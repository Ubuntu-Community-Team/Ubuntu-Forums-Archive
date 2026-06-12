---
title: "First Time Install Help Needed!"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Fingolfin269 on 2006-09-08
Hey everyone, I have finally succumbed to the desire to install what looks like a pretty neat OS.  I want to install Ubuntu on a laptop (2ghz/256mb ram) that I will use pretty much as a Firefox machine.  That's about all I require.

Anyway, is there a faster way to install this thing than loading it up off of CD and clicking the install icon?  The reason I ask is because when I double click the install icon it takes a very long time for an install window to even appear and when it finally does it is just white.  I let it go for about 15 minutes and nothing ever happened.  The CD kept going but I wasn't sure if there was an error or not because it never really said anything.

Any ideas?  Do I just need to leave it alone for a long time?

---

### Post by jordanmthomas on 2006-09-08
It takes a while on the LiveCD for me as well.  If it doesn't work you could try to download the Alternate installer (from the same place you got the desktop CD).  It's a text-based installer though, which scares some people.  

You could also go with the 'ol reboot and it'll probably work next time method.  :)

---

### Post by Fingolfin269 on 2006-09-08
Hey dude you live about an hour away from me so just come over here and fix it for me. :p (I'm in Murfreesboro)

I'm going to try this one more time with the GUI and then try the command line method if it doesn't work.  I hope I don't screw up partitioning this thing over because I really don't want to get rid of xp just yet.

---

### Post by jordanmthomas on 2006-09-08
..except that hour drive would cost me like 25 dollars.

---

### Post by Paul133 on 2006-09-08
Well, definitely do the text install and you can dual-boot with XP. If the text install doesn't work, then use the server install (on the alternate CD, too). If you do the server install, you'll get a commandline after you install, and just type ```
 sudo apt-get ubuntu-desktop 
``` Trust me, I had the same problem and this worked for me. It has to do with the RAM I think and the fact that you're on a laptop. If you want to dual-boot, follow this guide: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) Good Luck; if you need help, post on these forums and someone will definitely help you out (I'll try, too). And if you REALLY need my help, you can PM me.

---

### Post by Jukey on 2006-09-08
Nevermind, he fixed the error

---

### Post by Fingolfin269 on 2006-09-08
Okay, I just ran into another issue.

I'm running the alternate installer/text mode following a pretty extensive guide and I am having trouble at the partition section.  My HD is 40gb and I was going to leave 10gb for windows.  However, when I type in 10gb as the new partition size (or even 20gb) it just goes back to the primary screen showing #1 primary at 40gb still and no free space.

Any ideas?

I have defragged about 20 times and cleaned it up as well as I can.  Only 8gb of the 40gb is being used.

---

### Post by YeahBuntu on 2006-09-08
You need to use the Gparted program within the partition program to shrink your windows partition.  Most likely there is no free space because windows has formatted the whole drive.  Ubuntu is looking for space that has not yet been formatted.  Thats why you see no free space.  I am purdy sure. newbs helpin newbs.

---

### Post by Fingolfin269 on 2006-09-09
Well, I just tried out your suggestion (thanks by the way) and....

This is pretty maddening because it should be very simple.  I know I have around 75% of my drive free of data and yet even though I put in 20gb for my windows partition it still tells me 'Failed to create enough space for installation you will have to set up partitions manually'.

Oh well.  I don't really want to wipe windows completely yet but I am at a loss as to what to do now.  It tells me to partition manually but that does not work either.

---

### Post by YeahBuntu on 2006-09-09
Hmmm

Let me grab my crappy laptop and see whats going on (i'll run Gparted and see where you may be missing something)

---

### Post by YeahBuntu on 2006-09-09
Can you boot from the live CD?  Without installing... can you go to System.. Administration .. .Gnome partition editor ? Type what you see under partition.. filesystem etc..

---

### Post by Fingolfin269 on 2006-09-09
Sure, I will try that now.  The Live CD runs extremely slow on this laptop so it may be about 15-20 minutes.  I'll update ASAP.

---

### Post by bodhi.zazen on 2006-09-09
1. Boot to windows and defragment.

2. Back up any data you do not care to loose.

3. boot Ubuntu Live -> run Gparted -> resize windows partition.

4. Install ubuntu -> Installation process will partition and format the free space.

---

### Post by Fingolfin269 on 2006-09-09
> **YeahBuntu said:**
> Can you boot from the live CD?  Without installing... can you go to System.. Administration .. .Gnome partition editor ? Type what you see under partition.. filesystem etc..

I got in there and then couldn't get logged back into the forums so I am booting it up again now.  The information looked exactly the same as what I saw in the 'text' installation so I'm not sure if anything will work differently this time.

Here is what I see......

I have 2 lines under each of the columns.

First.  Partition: /dev/hda1 Filesystem: ntfs Size: 37.25GB Used: 8.22 GB Unused: 29.03GB Flags: boot

Second. Partition: unallocated Filesystem: unallocated Size: 7.84MB Used: --- Unused: ---- Flags: (blank here)


Does this help at all?

---

### Post by Fingolfin269 on 2006-09-09
> **bodhi.zazen said:**
> 1. Boot to windows and defragment.

2. Back up any data you do not care to loose.

3. boot Ubuntu Live -> run Gparted -> resize windows partition.

4. Install ubuntu -> Installation process will partition and format the free space.

Bah, I just tried using Gparted to resize and it went through the entire process of supposedly reducing my partition down to 12gb and then when it finally refreshed everything was back to the way it was before.

I'm starting to wonder if a) HP has done something to prevent people from 'accidentally' screwing up their system, b) something is wrong with my HD, or c) I am dumb. :)

---

### Post by YeahBuntu on 2006-09-09
WHen you run Gparted theres an option at the top to ACTUALLY DO what you want

So everything you do is imaginary until you click APPLY up at the top.

---

### Post by Fingolfin269 on 2006-09-09
Yup, I hit apply and it pulled up another box and my hard drive light was flashing for about ten minutes.  I checked up there again just to see if there was something I missed after it completed but all it would let me do was select 'resize' or 'copy'.

You guys have all been helpful and I appreciate it.  I think I'm going to fight with this for another half hour or so then go to bed.  Maybe the solution will come to me overnight. :)

---

### Post by YeahBuntu on 2006-09-09
You may want to try what bodhi.zazen's   suggested.  He has much more merit that what I know.

---

### Post by Fingolfin269 on 2006-09-09
> **YeahBuntu said:**
> You may want to try what bodhi.zazen's   suggested.  He has much more merit that what I know.

I can only get to 2.5 in his 4 step program.  I can't complete step #3 on this system for some reason.  I think I'll just wipe XP off of here completely tomorrow but I want to sleep on it before doing so since I can't find my restore discs. :p

---

### Post by pirate2001 on 2006-09-09
hello there - you know you're really stuck with this whole thing when you can't find out how to add a new post!!!!

That's me at the moment - I installed ubuntu last night and through a glitch, i've completely lost the ability to boot to either windows or ubuntu!!!!


i fear i may have lost my "work" data from xp...... f..........f.......fish cakes!!!

can someone please point me in the right direction. My hard drive is partitioned all over the place and the only way i can use my laptop now is via the cd drive!!

thank you all in advance

uregent help needed
 ps sorry i had to post on the backside of some one elses post - i am truly an idiot!!!!

---

### Post by Fingolfin269 on 2006-09-09
> **pirate2001 said:**
> hello there - you know you're really stuck with this whole thing when you can't find out how to add a new post!!!!

That's me at the moment - I installed ubuntu last night and through a glitch, i've completely lost the ability to boot to either windows or ubuntu!!!!


i fear i may have lost my "work" data from xp...... f..........f.......fish cakes!!!

can someone please point me in the right direction. My hard drive is partitioned all over the place and the only way i can use my laptop now is via the cd drive!!

thank you all in advance

uregent help needed
 ps sorry i had to post on the backside of some one elses post - i am truly an idiot!!!!

I don't mind you posting in here but I thought you would get more visibility with your own thread so I created one for ya.  Take a look. :)

BTW I inadvertently solved my problem.  I was trying to get this damn gpart to work and it finally made it to step 3... and crashed.  Now it doesn't recognize my primary partition so I guess Windows is gone.  Oops.

---

### Post by bodhi.zazen on 2006-09-09
> **Fingolfin269 said:**
> I can only get to 2.5 in his 4 step program.  I can't complete step #3 on this system for some reason.  I think I'll just wipe XP off of here completely tomorrow but I want to sleep on it before doing so since I can't find my restore discs. :p

If you could be a little more specific.....

first defrag you windows partition.

boot to ubuntu live cd.

Unmount the hard drive.
In a terminal:
```
sudo unmount /mnt/hda1
```
I am not sure of the mount point, may be /media/hda.

Then run Gparted and re-size. You do not need to format the free space you create.

I do not have access to Ubuntu right now so I am guessing. If you have problems I will check in later....

> Originally Posted by pirate2001
i fear i may have lost my "work" data from xp...... f..........f.......fish cakes!!!

You windows partition is still there, Gparted overwrote your partition table (unless you formated).

You may be able to rescue it if you know the exact size you windows partition was use Gparted to make a partition of that size where windows was. DO NOT FORMAT !!!

If that fails, try at a command line:
```
sudo unmount /mnt/hda1
sudo fdisk
```

If that fails, try creating one large partition on your hard drive. Again DO NOT FORMAT.

---

