---
title: "Very new.  Partionining help appreciated."
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by John L (UK) on 2006-08-16
Hi

First post - very much appreciate people's time and tolerance.

I've been given a working but wiped laptop from work.

Decided I should join the Linux movement and found my way to Ubuntu after quite a lot of browsing.

Managed to download and burn the ISO of Dapper.  As a piece of scoping context, this was a significant accomplishment for me.

Seems to run fine from CD and even managed to solve my wireless hookup by using these forums (thank you all again - people *do* search and what they find *is* valuable).

So two days ago tried to install to hard drive.  Get through to Step 5 of 6 where it asks to select a disk.....but it just sits with the rotating CD symbol whirring.  The graphical installer isn't giving me a list of drives.

I searched the installation Wiki and these forums.  The closest previous questions seem  to be around partitioning, but I don't know what that is beyond a vague understanding from Wikipedia.

My hypotheses - 
1.  The hard drive is, after all, broken.  Could this be true and the CD run still work??
2.  The Hard drive needs to be set up in some way that I haven't done?
3.  My CD of Ubuntu is broken.  I could re-download and reburn, but it took all night on my connection so I'm not wild on that one.

I guess I'm hoping it's #2 and someone will tell me how to fix it.  If it may be #1, how can I test?

I found the Disks Manager in the Ubuntu Systems folder.  It shows three disks:
1. Hard drive Unknown "tmpfs" with speed "not available"
2. hard drive Unknown "unionfs" with speed "not available"
3. CD drive

And that is as far as I can get on my own.  Probably trivial to IT literate people, so forgive me if I've not found the answer on my own.

The computer is a Toshiba Portege laptop with a Pentium III and 750ish Mb memory.

Thanks for any clues

John

---

### Post by mcneely.mike on 2006-08-16
when you boot into the cd, try one of the options such as nodma

at the boot screen it says to hit F1 / F2 etc for other options

see if that helps

---

### Post by xpod on 2006-08-16
Firstly and most importantly do not let yourself believe that "i.t experts" know it ALL because you`d be suprised at the problems some of them have on moving over to Ubunto(well....TRYING to move over..lol)

The 750omb should be more than enough to accomodate Ubunto but still you might need to try the "alternate" version which is the way to go when having problematic installs.

When i put Ubunto on my main pc it would`nt finish the install at the same part as you but merely by choosing "safe graphic mode"on startup of live cd seemed to work for me...After countless trys the normal way.

I had to though try other distos till eventually i found one that would install ok onto an older pc we have..That was the Kubunto one that eventually installed ok....Give it a good few goes and then consider trying the "alternate"version.

Somebody else will probably give you more technical advise but "welcome"anyway

EDIT:Dont mean to confuse but by"alternate"version i DONT mean another distro like Kubunto...IT means the "alternate Ubunto" version that dosent use a gui to install and so finds it easier to install.
You probably knew this but my last part there COULD be confusing..sorry

---

### Post by coffeecat on 2006-08-16
It may be that when the laptop was 'wiped' the disk label was wiped as well and this is confusing the installer. I had a similar issue when installing to a laptop and Gparted came to my rescue then. You can find Gparted after you have booted the live CD by going to System > Administration > Gnome Partition Editor. Post back with what that tells you, or go to Device > Set Disklabel and choose Disklabel type 'msdos'. Yes I know. Ghastly isn't it? :wink:

Hopefully you'll now have one HD showing as unallocated or unformatted. You could now go directly to the installer and it will offer to partition this unallocated space for you. If this doesn't work, just create a single whole-disc ext3 partition and go back to the installer. This partition won't last long because the installer has to create both a root (ext3) and swap partition. You could do this while in Gparted, but it's easier if you're new to Linux to let the installer do it for you. Others may suggest complicated partition setups with separate /home partitions and so on. I'd advise you to leave that geeky stuff until you have more experience with Linux. :) 

One thing I don't understand is the two hard drives showing in the Disk Manager. I thought laptops only ever came with one. Perhaps there's the remains of two partitions and this is confusing DM. It'll be interesting to see what Gparted shows.

---

### Post by xpod on 2006-08-16
HERE HERE...you told him what i was`nt sure HOW to tell him...haha
I also second leaving the multi-partitioning thing for now....
Give youself as little to do as possible to start with.
You`ll soon have plenty to do your self once it`s up and running.

EDIT: thats IF you get it going with this cd......IT just sounds a bit like how mine was at that same point.You`ll soon find out.

---

### Post by seshomaru samma on 2006-08-16
To me it sounds like your CD is broken . In my experience about 1/3 of the Ubuntu CD I burn don't work properly. Maybe it's my burner , or maybe beacuse I get them via Bit Torrent (never had a problem with an iso I downloaded from Ubuntu's servers) , not sure. 
If it was a problem with your harddisc you would have gotten some sort of error , I think. 
Did you check the CD for errors? you can do that when it boots
If you need to burn another CD - use the slowest possible speed.

---

### Post by John L (UK) on 2006-08-16
Thanks for all the advice so far.

I did do the CD check - no errors found.  I have requested a shipped copy to be safe.

I also found the Gnome partition editor you pointed to.  It says "no devices found" so I guess it's the hard drive??

Thanks

John

---

### Post by TMR on 2006-08-16
I'd suggest you download the 'alternate-install' cd iso and burn that.  Then try option 1, text-based install and let us know what happens

TMR

---

### Post by coffeecat on 2006-08-16
**John**, I've just realised that the two 'hard disks' listed by Disk Manager are probably virtual ones created by Ubuntu live in RAM. Tmpfs is a file system for storing files in virtual memory and I don't understand unionfs, but it's something to do with presenting several filesystems as one to the kernel. Anyway, the important, and depressing, thing is that Gparted can't see your HD. Did you try Device > Set Disklabel? It's probably greyed out but worth a double-check.

One long-shot thought. When your work 'wiped' your laptop, did they actually take the HD out? Rather than erasing it they may simply have removed it. It's quite possible, in which case you'll have to get hold of a replacement drive.

I can't really understand why others are querying whether your CD is bad. You stated in your first post that it runs fine and that you even got wireless working. That deserves a round of applause - to you. So I doubt whether it's a CD problem, although it won't do any harm trying a shipit copy. (Warning - shipit CDs can take a long time arriving.) Also, I don't believe the alternate CD is going to help here. Gparted is the graphical front-end for parted, and parted (as far as I know) is the partitioner used in the text-based alternate CD. If Gparted reports 'no devices found', then so will parted. But again, if you want to try, it's worth a shot.

---

### Post by John L (UK) on 2006-08-16
Hi everyone

The hard drive is present (I've just taken it out and put it back - another first for me!).

I think i have come to the conclusion that it's broken.

I have tried loading Windows 98 from the OEM CD I have with my desk computer - and that too reports it can't find a Hard Drive.

So, I'll find a hard drive and have another go.  Will I need to do anything to it once it's in - format? drivers??  I hope not, 'cos I've no idea how to do either of these things!!

Anyway, if you see this thread rise up again it'll either be bad news or good...

: )

John

---

### Post by coffeecat on 2006-08-16
**John**, sorry to hear the HD is broken. :( I think all you have to do to initialise a new HD would be to go through the steps with Gparted that I listed in my earlier post. One tip - if you're tempted to pop down to your local PCWorld, you'll find that laptop-sized HDs - even the brown-box OEM ones - are very expensive there. I wanted a spare one for a project and ended up dissecting a dead laptop (which fortunately had a perfectly good HD) to get one. Suggest you shop around on the online stores if you can't find a defunct laptop.

Best of luck.

Edit: no - you won't need special drviers for a replacement drive. It's all in the Linux kernel.

---

