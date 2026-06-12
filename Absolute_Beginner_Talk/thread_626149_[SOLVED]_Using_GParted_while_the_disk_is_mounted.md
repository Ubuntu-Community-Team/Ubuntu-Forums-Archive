---
title: "[SOLVED] Using GParted while the disk is mounted?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-28
I have used Ghost for Linux --- oooppss Symantec's attorney's nixed that name.

I have used G4L to clone my former boot drive to a new 320 gig drive.

I want to use GParted to both resize and move the partition. Well, technically if I can make my current /dev/sda1bigger than 16gig, that is make it 280 gig, I'll be in hog heaven.

I've played around with GParted, but done nothing as I can't recall whether it has to be run as a LiveCD session.

Mounted drives cannot have partitions modified: Yes OR No???

---

### Post by Pumalite on 2007-11-28
I would go with Gparted Live CD. Drives should not be mounted, to partition.

---

### Post by -grubby on 2007-11-28
you should not partition mounted drives, I don't even know if GPARTED let's you. Here's the [GPARTED LIVE-CD]("http://gparted-livecd.tuxfamily.org/") that runs without mounting any hard drives

---

### Post by mikewhatever on 2007-11-28
Is it really so hard to find gparted documentation?
[http://www.google.co.il/search?q=gparted+documentation&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.il/search?q=gparted+documentation&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by Mark_in_Hollywood on 2007-11-28
Is it really so hard to find documentation?

Maybe not for you. That is mox-nix here, anyway. 

GParted LiveCd first wouldn't load a graphic GParted.

Once loaded, I found my "unformatted" 279gig as /dev/sda4. I couldn't not get it to add itself to /dev/sda1 (15.63 gig)  nor could I move the /dev/sda1 to /dev/sda4; which was probably not the best idea I've had all day, anyway.

OK, kind folks. I have a partiton I would prefer to "move" to /dev/sda1. I'm looking at the documentation. I'm sure I don't understand this all that well. I believe "move" is only for between devices (harddrives)? 

Just a little more help with how to get the unused 279gig into /dev/sda1, please.

---

### Post by CatKiller on 2007-11-29
> **Mark_in_Hollywood said:**
> Just a little more help with how to get the unused 279gig into /dev/sda1, please.

What you're asking would require a screwdriver. Seriously.

You have some options, and it really depends on what you are trying to achieve.

If you want to replace your existing hard drive with the new one, you can use dd, Gparted, G4L or whatever to copy the existing information to the new hard drive. It's important that you copy the existing MBR (Master Boot Record) to the new drive, since that's where GRUB lives. If you don't, then you'll need to install GRUB into the new drive, which isn't hard, but is an extra step. Then you can use Gparted to increase the size of the partitions on the new drive to take up the whole disk. Turn the computer off, whip out the old drive, set the jumpers correctly, put the new one in its place, and Robert's your father's brother.

However, it is possible to use both of these drives at the same time. The Linux filesystem structure has everything as a file as part of a tree that starts at /, which is why / is sometimes called "root". Strictly speaking, as part of the boot process a filesystem gets mounted at /, and then later, filesystems can get mounted at other points - /media/cdrom, for example, or /home. There are very few restrictions on where things are mounted, and you can have some quite exotic configurations. When you mount a filesystem at a mount point, it overlays whatever is there - usually it is just an empty directory - replacing those contents as far as everyone is concerned. When you unmount that filesystem, the previous contents re-appear, since they were underneath all the time. Some people use this behaviour to have a local backup of network-stored configurations so that normally the network is used, but if the network is unavailable then people can keep working.

Many people use this functionality to have their /home folder on a separate partition. There is no difference in terms of how it is used to have /home as a folder, /home on a separate drive, /home on the network... This is handy, since all of a users configuration and data are normally kept in their Home folder, so if something goes wrong, or they want to switch to a different distribution or what-have-you, they can install over one partition and all of their data is still intact and their configuration is ready to be seamlessly used with the new installation. See, for example, [here]("http://www.psychocats.net/ubuntu/separatehome"). Basically, you make a new partition of whatever size on whatever device you like, copy your existing data to it with cp, tar, or whatever, and then use /etc/fstab to determine where in your file structure you would like this information mounted.

If you let us know exactly what you're trying to achieve and how far you've got, someone should be able to give you more detailed instruction.

---

### Post by Mark_in_Hollywood on 2007-11-29
I used G4L. Past tense. The old drive of 20 gig, was bit copied to the new 320 gig drive. Only problem is there is appox. 287 gig "unallocated". When I try to "resize/move" it leaves behind about a 4 gig partition that is not much use and I would have to do that 5 times to "resize/move" the unallocated space up to /dev/sda1.

Anybody know how to allocate the space to sda1?

---

### Post by Mark_in_Hollywood on 2007-12-07
After way to much sweat, do to the fear of damaging the file system or the stored data, I have managed to make (and mount) a working OS.

This type of work isn't for beginners. It's too bad there isn't a unique support group at the Forum to handle peoples needs. It's one thing if you have one hard drive and add Ubuntu exclusively, another if you must have M$ products and a third if you are moving "everything" from a small drive to a larger.

User friendly won't even begin to apply until that bar is hurdled.

otherwise: solved.

---

### Post by CatKiller on 2007-12-10
> **Mark_in_Hollywood said:**
> This type of work isn't for beginners.

See, you've hit the nail on the head there. Beginners aren't going to be doing what you were doing. It is, however, quite straightforward, and you can do it all in a point-and-click interface.

---

### Post by Gotit on 2007-12-11
Mark, I am happy to hear you have conquered your Everest, however, I am still sitting in the base camp looking up!

I have a similar situation and could use a hand.  I had a 40GB drive and used G4L to make an image of it.  I then replaced the 40GB with a larger 160GB drive to which I restored the 40GB image.  I had hoped that when I restored the image it would have found the additional disk space and allocated it to the file system.  Unfortunately, I was left with a 37GB file system partition (hdb1), a 2GB extended partition (hdb2), a 2GB swap partition (hdb5) and 110 unused area.

I used GParted to partition and format the unused area of the new drive.  The result was I now have a new partition (hdb3) along with the partition as listed above.  My quest is to allocate the new partition area (hdb2) to the file system and in essence have one linux drive/partition that is approximately 150 – 150GB in size.

Also, I booted from a CD with GParted and tried to find a way to re-allocate partition size to make by file system us all (or as much as possible) of the drive, but no joy there.  I could reduce the size of the existing file system partition but it doesn't appear I can utilize any of the new 110GB partition.

So, where do I go from here?

---

### Post by CatKiller on 2007-12-12
You can boot up with the cd and use GPartEd to remove the new partition and resize the existing partitions into the free space by dragging the right-hand edge. You may need to unmount your swap partition since some live cds utilise the swap space for performance reasons, but as stated above you cannot edit a mounted partition.

Alternatively, you could move your /home to the new partition and mount that partition as your /home - since that is where you are most likely to keep your stuff (technical term, you understand). Or you could mount that partition arbitrarily in your filesystem for general data.

See, for example, [here]("http://gparted-livecd.tuxfamily.org/larry/resize/resizing.htm") for information about resizing, or[here]("http://www.psychocats.net/ubuntu/separatehome") for information on having a seperate /home partition.

---

### Post by Gotit on 2007-12-12
OK, that pretty much work for me, thanks.
One final question, when I started my drive in GParted showed as:
Ext3 (35GB) Extended/swap (1.5 GB each) Unallocated (111GB)
in that order.  I turned swap off and deleted it.  

Then I moved the Extended partition to the (right) end of the Unallocated section and left it at 1.5GB.
Then I increased the size of the Ext3 partition to the beginning of the Extended partition.  So the layout looked like:
Ext3 (124GB) Extended (1.5GB)

I found no way to turn swap back on, don't know if that matters.  Should I have, or could I have deleted the Extended partition and claimed the whole disk for Ext3 partition?

---

### Post by CatKiller on 2007-12-13
An Extended partition is one that can have more partitions inside it. See, for example, [here]("http://en.wikipedia.org/wiki/Disk_partitioning") for the differences between Extended partitions, Primary partitions, and logical drives.

It is, in general, useful to have a swap partition. The way to create one, for you, is to simply create a new logical partition inside that Extended partition and assign it to swap.

If you really don't want [swap]("http://en.wikipedia.org/wiki/Swap_space#Swapping_in_Linux") then you can delete that Extended partition and expand your ext3 partition even further.

---

### Post by Gotit on 2007-12-13
Well, I got a new swap all set up and it shows "swapon" in GParted, but I don't think the system sees it?
steve@Home-Ubuntu:/proc$ cat meminfo
MemTotal:       905460 kB
MemFree:        500244 kB
Buffers:         11860 kB
Cached:         213028 kB
SwapCached:          0 kB
Active:         200944 kB
Inactive:       145376 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       905460 kB
LowFree:        500244 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:              52 kB
Writeback:           0 kB
AnonPages:      121484 kB
Mapped:          42324 kB
Slab:            16728 kB
SReclaimable:     8420 kB
SUnreclaim:       8308 kB
PageTables:       1704 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:    452728 kB
Committed_AS:   470768 kB
VmallocTotal:   114680 kB
VmallocUsed:     46712 kB
VmallocChunk:    64496 kB
-----------------------------------------

However, if I turn swap on from the command line, it seems to show up:
steve@Home-Ubuntu:/proc$ sudo swapon /dev/hdb5
[sudo] password for steve:
steve@Home-Ubuntu:/proc$ cat meminfo
MemTotal:       905460 kB
MemFree:        425972 kB
Buffers:         12976 kB
Cached:         245080 kB
SwapCached:          0 kB
Active:         250184 kB
Inactive:       168500 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       905460 kB
LowFree:        425972 kB
SwapTotal:     1646620 kB
SwapFree:      1646620 kB
Dirty:             112 kB
Writeback:           0 kB
AnonPages:      160680 kB
Mapped:          60536 kB
Slab:            17476 kB
SReclaimable:     8820 kB
SUnreclaim:       8656 kB
PageTables:       1952 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2099348 kB
Committed_AS:   610872 kB
VmallocTotal:   114680 kB
VmallocUsed:     47524 kB
VmallocChunk:    64496 kB
steve@Home-Ubuntu:/proc$ 
------------------------------------------

But when I re-boot, swap is back to 0kB

Is this right??

---

### Post by CatKiller on 2007-12-13
Edit which partitions get mounted where by ```
gksudo gedit /etc/fstab
``` Look for a line that says ```
/dev/hda5       none            swap    sw              0       0

``` If there isn't a line like that there, add it. It obviously got removed when you booted with no swap partition.

---

### Post by Gotit on 2007-12-13
Thanks for the fstab tip.  
The line was in there but it had a different UUID associated with that partition than what blkid showed.  I copied the UUID shown in blkid and pasted it in fstab and now all works fine.:)

---

