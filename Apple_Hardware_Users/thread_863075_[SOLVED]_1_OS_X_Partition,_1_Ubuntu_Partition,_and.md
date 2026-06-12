---
title: "[SOLVED] 1 OS X Partition, 1 Ubuntu Partition, and 1 shared between them"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by Mattaus on 2008-07-18
I have recently installed OS X 10.5, and Ubuntu onto a 3,1 Macbook Pro using the rEFIt method. After a little fiddling around I could get OS X to read the Ubuntu partition, and vice versa. Write would not work.

However after an attempt to relax a little I plugged my iPod in and discovered that both Ubuntu and OS X could read and write from the thing fine. It might be important to note that up until this point my iPod had been used exclusively on my Vista Desktop. 

Anyway, it got me thinking - can I partition up my HDD so that there is say 25GB to OS X, 15GB to Ubuntu (+1GB swap space) and then the rest of the Hard drive (roughly 79GB) as a blank partition that could effectively act as an internal version of my iPod? Like a shared drive basically.

I only ask this because the only things I'd share between the 2 installs are photos, videos, music and my various creations in GIMP/Photoshop, so why store them all over the place and go about the difficulty of having to access them from differently formatted drives etc etc. (and thus allowing me to keep my OS X drive Journal'd)

So basically what kind of format would that swap drive need to be to allow the OS X and Ubuntu installs to read and write to with minimal fuss, and what could I use to do it with? I tried the OS X installer DVD but that wouldnt allow me to do it (which raised another issue - can I do this without erasing my installed OS's or will I have to start from scratch?) and is there something in Ubuntu that could help? GParted maybe?

Obviously I'm a bit of a newbie so any help or a point in the right direction would be greatly appreciated.

Cheers.

---

### Post by schauerlich on 2008-07-18
NTFS is readable and writable from both OS X and Ubuntu once you install the ntfs-3g package from the repos.

```

sudo apt-get install ntfs-3g

```

---

### Post by ad_267 on 2008-07-18
You can use the Ubuntu live cd with gparted on it to shrink the Ubuntu and OSX partitions and then create a new partition for sharing the data.

---

### Post by Mattaus on 2008-07-18
Will resizing the partitions wipe them? I guess there's only one way to find out really.

---

### Post by schauerlich on 2008-07-18
You can nondesructively shrink OS X's partition with Boot Camp. Start it up (/Applications/Utilities/Boot Camp.app) and start the installer. Use it to shrink your OS X partition to the size you like, and then quit the installer before you get to downloading the driver CD and everything. This may not work if you've already installed Ubuntu, since Boot Camp can't see more than 3 partitions.

---

### Post by Mattaus on 2008-07-18
Ah I see. Kinda late now - GParted is busy doing it's thing as we speak lol. I'll see how it goes.

Thankfully I haven't really got into any massive installs yet as I only got the laptop 2 days ago and have never used OS X before, so I'm kinda learning the ropes at the moment.

---

### Post by schauerlich on 2008-07-18
> **Mattaus said:**
> Ah I see. Kinda late now - GParted is busy doing it's thing as we speak lol. I'll see how it goes.

Thankfully I haven't really got into any massive installs yet as I only got the laptop 2 days ago and have never used OS X before, so I'm kinda learning the ropes at the moment.

Hope things go alright, OS X and Ubuntu are my two OS's of choice, so you're alright in my book. :)

Just remember to make the storage partition ntfs and install ntfs-3g on Ubuntu and you should be fine

---

### Post by Mattaus on 2008-07-18
I'm trying OS X as I'm fed up with Vista on my desktop. So if It all goes well on my laptop....

So far I'm impressed lol. Though I'm having difficulty getting used to the track pad. I rarely use those things.

---

### Post by schauerlich on 2008-07-18
> **Mattaus said:**
> I'm trying OS X as I'm fed up with Vista on my desktop. So if It all goes well on my laptop....

So far I'm impressed lol. Though I'm having difficulty getting used to the track pad. I rarely use those things.

Make sure to enable two finger scrolling and right click. Once you get used to those, you'll wonder how you ever got by without them.

For future problems, be sure to bookmark these two pages:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I can guarantee you they will save you loads of time waiting for responses on the forums. I speak from experience. :) If only I learned it sooner.

Happy computing!

---

### Post by Mattaus on 2008-07-18
ahahaha.

Cheers dude.

---

### Post by cyberdork33 on 2008-07-18
NTFS is a good choice, but a little slower than FAT32, however, there is a 4GB filesize limitation in FAT32... Your iPod is likely a FAT32 filesystem.

---

### Post by Mattaus on 2008-07-18
Funny, my iPod is the first gen nano, and is 4GB. :)

I'm busy mucking around with my partitions to get the 2 OS's their own partitions, and then a large NTFS formatted partition for them to share.

I'll obviously be back if I have problems - which judging from the first try I will! (though I'm trying to work it out myself first!)

Cheers

---

### Post by Mattaus on 2008-07-18
Question - When I'm formatting the shared NTFS partition, should it be 'primary' or 'extended'? I've never really mucked around with this sort of stuff before so I'm kind of unsure.

Any help would be greatly appreciated.

EDIT:

ARGH!!!! I formatted the final partition as a Primary NTFS drive, and now when rEFIt starts up I get the MAC OS X logo, 2 Tux HDD logos, then a Windows logo and finally the Tux CD logo. EXCEPT now when I tried to boot into Linux off the HDD (which was working fine), it had the boot problems again. So I synced the partitions, then when I tried to boot onto the live CD to fix the frozen tux logo, it freezes on that! So I can't boot the Live CD to fix the problem. From where I sit the only way to fix it is to wipe ext3, swap and NTFS partitions from within OS X, then start it all again.

Why did it screw up? 

Also, I've noticed that even though there is a 70GB NTFS partition on the drive, I cannot see it from within OS X. I thought OS X and ubuntu could read and write to NTFS fine? Or am I going to have to muck around with getting OS X to read that as well? Oh, and I made the OS X drive 35GB, but now I can't make it bigger again. I was going to wipe all the drive bar OS X, and make OS X the full HDD again, then use Boot Camp to divide the drive up. Can I make OS X the full drive again? I'm at the point where I'm ready to wipe the whole thing and start everything from scratch. Not that it would help because it puts me right back where I started.

I'm so lost.

---

### Post by cyberdork33 on 2008-07-18
> **Mattaus said:**
> Funny, my iPod is the first gen nano, and is 4GB. :)
It is not a partition-size limitation, it is a filesize limitation. For example, trying to copy a 9GB DVD iso to a FAT32 partition would fail, However, copying 9 1GB files would work fine.

> **Mattaus said:**
> ARGH!!!! I formatted the final partition as a Primary NTFS drive, and now when rEFIt starts up I get the MAC OS X logo, 2 Tux HDD logos, then a Windows logo and finally the Tux CD logo. EXCEPT now when I tried to boot into Linux off the HDD (which was working fine), it had the boot problems again. So I synced the partitions, then when I tried to boot onto the live CD to fix the frozen tux logo, it freezes on that! So I can't boot the Live CD to fix the problem. From where I sit the only way to fix it is to wipe ext3, swap and NTFS partitions from within OS X, then start it all again.That's what I would do. Note that there are some partitioning issues on Macs, though you should be able to make your NTFS partition last like you trying to since it won't be bootable.

> **Mattaus said:**
> Why did it screw up? I don't know what you did, so I have no idea.

> **Mattaus said:**
>  Also, I've noticed that even though there is a 70GB NTFS partition on the drive, I cannot see it from within OS X. I thought OS X and ubuntu could read and write to NTFS fine? Or am I going to have to muck around with getting OS X to read that as well?You need MacFUSE and the ntfs driver to get that working. NTFS will work in Ubuntu without configuration.

> **Mattaus said:**
> Oh, and I made the OS X drive 35GB, but now I can't make it bigger again. I was going to wipe all the drive bar OS X, and make OS X the full HDD again, then use Boot Camp to divide the drive up. Can I make OS X the full drive again? I'm at the point where I'm ready to wipe the whole thing and start everything from scratch. Not that it would help because it puts me right back where I started.
I would suggesting reading a bit before you go doing stuff. gparted (and other open partition editors) are unable to 'grow' or increase the size of HFS+ partitions. There are not a lot of details on the specifics of HFS+ which make it a difficult system to deal with outside of OS X. If you have Leopard, you should be able to start Disk Utility and resize your OSX partition back to the whole drive.

Get the OSX partition back to the size you want, then use gparted on the livecd to create all the other partitions you want before you install anything.

---

### Post by Mattaus on 2008-07-19
Ah ok.

I've just dislocated my shoulder for the second time in 4 months so I may not get round to it straight away (im on pain killers for the next week minimum damnit) but when i do i'll let you know how it goes.

Thanks for your help so far!

---

### Post by Mattaus on 2008-07-19
Hmmm

I turned the shared drive into 1 large FAT32 partition. It works great from the Ubuntu side of things in that I can read write to it - but I have no idea how to make it visible under OS X. If I go to disk Utility and try and mount it, it says it can't.

I was under the impression that OS X could read/write to FAT32 natively? Is there anything special I need to do in OS X to be able to see the Shared drive?

EDIT: I found an old post that you replied to cyberdork33 regarding this exact problem (sorry I forgot to take note of the thread) and basically it boils down to a Microsoft reserved flag (msftres) that gparted sets when it formats the FAT32 drive. According to the solution OS X can still mount it in Disk Utility even though its grayed out. Unfortunately I have found this to NOT be the case. I even went back in GParted and changed the flag to HP-something-or-rather ('no flag' is not an option it seems) That did'nt work either. Try as I might I cannot get OS X to mount the FAT32 drive.

---

### Post by cyberdork33 on 2008-07-19
> **Mattaus said:**
> I was under the impression that OS X could read/write to FAT32 natively? Is there anything special I need to do in OS X to be able to see the Shared drive?
It can. As you mentioned in the rest of your post there is some weird issue. You could probably use gparted to delete the FAT32 partition completely, then use diskutility to create a new FAT32 partition (msdos) in its place. Then OS X should set the flags as needed.

---

### Post by Mattaus on 2008-07-19
*sigh*

I deleted the partition, loaded up the disk utility off the Mac OS X disk, selected the main disk, clicked the '+' icon and tried to create the FAT32 partition out of the remaining HDD space. As soon as i clicked apply it said "MediaKit reports no such partition" and promptly does nothing.

I'm deleting the Linux Install (along with its swap space) increasing the OS X partition to the full size of the drive and starting again...though I have no idea what to do differently this time.

Sorry this is dragging on people.

EDIT: MAC OS X Disk Utility is the most useless thing I've ever used. Not one thing I have told it to do, it has actually done. I've now deleted the Linux partitions (using GParted) and tried to increase the size of the OS X Partition to take up the whole disk using Disk Utility - wont do it. I tried to create a new Partition - wont do it. It won't do ANYTHING. It always comes up with an error. Hell 90% of the time it says it can't format it yet when I go into GParted it has done it anyway. The changes never get reflected in Disk Utility. I never thought it would be so difficult to just partition a HDD up. ffs it just failed trying to create a second HFS+ drive. It's useless. It can't even create its native drive format.

---

### Post by cyberdork33 on 2008-07-19
> **Mattaus said:**
> *sigh*

I deleted the partition, loaded up the disk utility off the Mac OS X disk, selected the main disk, clicked the '+' icon and tried to create the FAT32 partition out of the remaining HDD space. As soon as i clicked apply it said "MediaKit reports no such partition" and promptly does nothing.

I'm deleting the Linux Install (along with its swap space) increasing the OS X partition to the full size of the drive and starting again...though I have no idea what to do differently this time.

Sorry this is dragging on people.

EDIT: MAC OS X Disk Utility is the most useless thing I've ever used. Not one thing I have told it to do, it has actually done. I've now deleted the Linux partitions (using GParted) and tried to increase the size of the OS X Partition to take up the whole disk using Disk Utility - wont do it. I tried to create a new Partition - wont do it. It won't do ANYTHING. It always comes up with an error. Hell 90% of the time it says it can't format it yet when I go into GParted it has done it anyway. The changes never get reflected in Disk Utility. I never thought it would be so difficult to just partition a HDD up. ffs it just failed trying to create a second HFS+ drive. It's useless. It can't even create its native drive format.
I understand your troubles... Disk Utility doesn't like "free space" The add partition function is really meant to divide your OSX partition in two, (reducing the size of the OSX partition, and creating a new partition with the difference).

There is a trick however... With just OSX, and the rest f the drive blank, start Boot Camp. It should allow you to create a windows partition by reducing the OSX partition. Go ahead and do that making the new partititon as small as you can (I know this seems backwards but stick with me). Then, after rebooting, start Boot Camp again to "restore" the drive to OSX only. This will magically stretch your OSX partition to the rest of the disk.

The other option other than Disk Utility is to do everything from the commandline with 'diskutil resizeVolume'. See some instruction here:
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

---

### Post by Mattaus on 2008-07-19
lol, I cant win.

I've just erased everything - i have it now creating a 35GB HFS+ partition, a 60GB FAT32 partition, and leaving 17GB as free space.

I'm HOPING I can then do a fresh install of OS X to the HFS+ partition, and install Linux to the 17GB free space. In all of this i'm praying the 60FB FAT32 actually gets formatted correctly and stays that way.

Though its not looking good because its now been thinking for close to 2hrs and nothing has happened yet....

---

### Post by cyberdork33 on 2008-07-19
you just have to make sure that your Ubuntu root partition is number 4 with the swap after or just have no swap at all and make a swapfile afterwards. There is a 4 partition "limit" on the emulated MBR, and grub uses this to boot, so anything beyond #4 cannot be booted from GRUB (AKA Linux)

---

### Post by Mattaus on 2008-07-19
Ah ok...i'll remember that if it ever gets there. The drive is only 120GB and its been formatting it for 3hrs now. Should I be worried thats its completely rooted it now?

---

### Post by cyberdork33 on 2008-07-20
> **Mattaus said:**
> Ah ok...i'll remember that if it ever gets there. The drive is only 120GB and its been formatting it for 3hrs now. Should I be worried thats its completely rooted it now?
not necessarily. That does seem long though.

---

### Post by Mattaus on 2008-07-20
After 4hrs i hit stop and stuck in my original OX 10.4 DVDs. It saw 2 partitions and free space equivalent to what i had asked 10.5 to do...so i formatted them both (which it did fine) and installed 10.4 to the 35GB partition.

I'm busy upgrading back to 10.5 and so far so good. I quickly cheacked while in tiger if it saw the FAT32 disk in Finder, which it did. Leopard even saw the tiger install and 60GB of FAT32 when I stuck the installer disk in.

Fingers crossed it will work now. Though my problems didnt begin till I installed Linux last time...

---

### Post by Mattaus on 2008-07-20
Right...OS X installed fine. I did however put rEFIt on and reboot with 8.04 disk in there...rEFIt boot screen never showed up. I tried installing it again but it did the same thing...

So I figure maybe its cause I haven't updated 10.5 yet? Im updating it now but if this does not work I'm seriously considering giving my hopes of an Ubuntu/OS X dual boot a miss and going with 100% OS X. I'm just a tad annoyed lol.

---

### Post by Mattaus on 2008-07-20
OMG!!!!

I got it working lol. 

What i tried last worked. I now have a OSX drive, ubuntu drive and a shared drive. With full read/write to the shared drive from both OS's.

Thanks to all that helped!

---

