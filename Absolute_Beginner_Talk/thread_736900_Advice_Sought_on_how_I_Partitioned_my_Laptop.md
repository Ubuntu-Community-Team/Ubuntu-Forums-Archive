---
title: "Advice Sought on how I Partitioned my Laptop"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-27
Greetings

I recently learnt manually to install Ubuntu on my laptop, a Sony Vaio VGN-S3; I did it with the 60 gb hard drive thus:

1st partition: 15gb for ubuntu, ext3, mounted as "/"
2nd partition: 10gb for a partition, ext3,  mounted as "/home/"
3rd partition:2.5gb for a partiton, ext3,  mounted as "/swap/"
4th partition: 22+ gb for a partition, FAT32, mounted as "/XPDATA/"

The installation thus far seems to be working extremely well, but I am beginning to think that it may be a good idea to install again, and I think the FAT32 partition may not have been a good idea.

The reason for my concern is that when I go to shut the system down, lines of writing appear, then the Ubuntu orange bar moves across and then, more often than not, it just
"hangs" with that still shot on the screen and I have to hold down the off button on the laptop to force it to spin down.

Can anyone suggest why this annoying problem may have occurred, and suggest an installation plan for me to try, which would hopefully fix the problem?

I am quite happy to reinstall as this laptop is currently a spare and I work on my desktop which thus far has remained very stable.

Regards

John

---

### Post by niteshifter on 2008-03-27
Hi,

Multiple partitions are not a problem - my last Ubuntu laptop had 11. What does look odd is the third:
> 3rd partition:2.5gb for a partiton, ext3, mounted as "/swap/"

I'm not near my home system with all the notes and such, but I think that's going to make Ubuntu use a swap file instead of a swap partition.

Could you post the output of this command: (that's a lower-case L after the dash)
```
sudo fdisk -l
```
so we can see the precise partitioning information?
--

As to the FAT32 thing: It depends. This Vaio is a pure Linux box, no windows install so it doesn't really make sense to use FAT. It's a simple file system, but not very robust (in terms of error handling / error correction - it has the bare minimum and none respectively). Using FAT - type file systems makes some sense if one is moving files between Ubuntu and a Windows installation in the same box.

---

### Post by Andavane on 2008-03-27
> **niteshifter said:**
> Hi,

Multiple partitions are not a problem - my last Ubuntu laptop had 11. What does look odd is the third:


I'm not near my home system with all the notes and such, but I think that's going to make Ubuntu use a swap file instead of a swap partition.

Could you post the output of this command: (that's a lower-case L after the dash)
```
sudo fdisk -l
```
so we can see the precise partitioning information?
--.
Certainly. The information is:

> andavane@andavane-desktop:~$ sudo fdisk -l
[sudo] password for andavane:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2553    20506941    7  HPFS/NTFS
/dev/sda2            2554        3026     3799372+  12  Compaq diagnostics
/dev/sda3            3027        4865    14771767+   f  W95 Ext'd (LBA)
/dev/sda5            3027        3494     3759178+   b  W95 FAT32
/dev/sda6            3992        4534     4361616    7  HPFS/NTFS
/dev/sda7            4535        4865     2658726    b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88086b9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14219   114214086   83  Linux
/dev/sdb2           14220       14593     3004155    5  Extended
/dev/sdb5           14220       14593     3004123+  82  Linux swap / Solaris
andavane@andavane-desktop:~$  

I'll be very interested as to what you read here.

> As to the FAT32 thing: It depends. This Vaio is a pure Linux box, no windows install so it doesn't really make sense to use FAT. It's a simple file system, but not very robust (in terms of error handling / error correction - it has the bare minimum and none respectively). Using FAT - type file systems makes some sense if one is moving files between Ubuntu and a Windows installation in the same box  
It doesn't make sense to me now either.
Originall the plan was to have it so I could read my files with Windows XP as well as linux, but I accidentally wiped my XP, so with that the need for this went out of the Window!
I realised it was a bit silly after I'd made the installation...

Looking forward to your opinion.

best wishes
John

---

### Post by stalkingwolf on 2008-03-27
You might also want to increase the size of your / partition a bit.  As I found just the other
day it is quite easy to fill that small a partition.

---

### Post by dsauxier on 2008-03-27
You may not have trashed the Windows partition.  If you mount sda6 there should be a boot.ini file.  Change the boot partition from 0 to 5 (possibly to 6) and it may fire up.

If you're going to reinstall, it might be a good time to break out the Windows recovery disk and put that back on (did I just say that?)

You don't "need" a /home partition, it will live on "/" just fine and that gives you the benefit of  combining those two partitions.

---

### Post by niteshifter on 2008-03-27
Ok, this is what I see from fdisk's report:

There are two hard drives in the system:

The first one (/dev/sda) is 40 GB. 
The second one (/dev/sdb) is 120 GB. 

On the first one are these partitions:
sda1: A primary partition of 20506941 x 1024 = 20.9 GB
sda2: A primary partition of 3.9 GB
sda3: An extended partition (contains the logical partitions)
sda5: A logical partition of 3.8 GB
sda6: A logical partition of 4.4 GB
sda7: A logical partition of 2.7 GB

Total (approx) 35.7 GB. The missing space is "between" sda5 and sda6, sda5 ends on cylinder 3494, sda6 begins at cylinder 3992, so:
3992-3495 = 497 cylinders
497 x 8225280 bytes/cyl = 4.1 GB unused.

Math check: 35.7 + 4.1 = 39.8 GB. Close enough to 40 GB.

I admit to being a bit baffled here. It's a Sony Vaio, but with a partition (sda2) marked as Compaq diagnostics. That is more likely a recovery partition (DVD image | CD images), 3.9 GB is an awful lot of diagnostic ware!


Now for the second drive. It has these partitions:
sdb1: A primary of 116.9 GB
sdb2: An extended partition.
sdb3: A logical partition of 3.0 GB

Total (approx) 119.9 GB. Math checks ok, no missing space.
This, I think, is where Ubuntu is. You are using a swap partition (sdb5) which is the best way to handle swap. The layout on this drive looks very much like an Ubuntu install done with default choices. For example here's mine (a Dell factory install of 7.10 on a 1420N):

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11         663     5245222+   b  W95 FAT32
/dev/sda3   *         664       14021   107298135   83  Linux
/dev/sda4           14022       14593     4594590    5  Extended
/dev/sda5           14022       14593     4594558+  82  Linux swap / Solaris
```
(sda2 is OS recovery. sda3 is /boot. sda5 is the swap, and why Dell / Canonical sets a 4.5 GB swap on a 2 GB RAM machine is odd - that's a bit much - unless this is a one-size-fits-all approach for a machine that comes standard with 1GB but can have up to 4GB)


Conclusions:
A Vaio VGN-S3 has two hardrives? That's unusual, but a google search kind of indicates that, but I could not find any technical materials on Sony's site for this machine. The only thing that's definitive is /dev/sda was the Windows' C: drive. Assigning Win drive letters to the remaining possible drives (partitions) would be pure speculation on my part.

It's possible (that's mostly speculative, btw) that Windows could be recovered - if you really, really need it - by using the recovery partition (sda2) but I've no idea how (more googling needed). Somewhat easier would be to use a SuperGrub CD perhaps (if GRUB was installed, that is).

Also, any files that were on C: (sda1) may possibly be recovered by mounting that partition and using ntfs-3g. Same for any on sda6. Also possible with sda7 (but you would not need ntfs-3g for that). Windows XP boot control is in a file named boot.ini which might still be there, somewhere.

Easiest is to completely re-install the OS or OSes of your choice. If that's your choice, then you've partition decisions to make, and friend, you've got all kinds of options there :) If you decide you want windows and Ubuntu do the windows install first!

---

### Post by Andavane on 2008-03-27
Oh SORRY I feel such an idiot!   :rolleyes:
What a stupid burk I am!
I took the reading from the desktop machine which has two hard drives.
I feel a complete dipstick.
OK going over to the laptop now to get that report...
Regards
John

---

### Post by Andavane on 2008-03-27
niteshifter here's the report from sony laptop:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc755b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        7296    58605088+   5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
/dev/sda6               1        1824    14651185+  83  Linux
/dev/sda7            1825        3040     9767488+  83  Linux
/dev/sda8            3041        6079    24410736    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 4110 MB, 4110188544 bytauxieres
128 heads, 63 sectors/track, 995 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         992     3999712+   b  W95 FAT32
andavane@ramanavayubuntu:~$ 

and once again apologies for giving the runaround - it was a tiring night...
Look forward to hearing from you.

NB: DSauxier, I had earlier and inadvertently selected "Guided/use entire disk" when installing so think I may have wiped the entire drive.
However when the PC was new, they advise making two dvd's for backing up windows, which I did. So I guess I could see if it reinstalls from them. I'd probably need to go to the sony website to remind myself (it has been three years) how to do this.

Thanks to all for your indulgence and patience.

Regards

John

---

### Post by niteshifter on 2008-03-29
Hi John,

Don't worry about the error, we all have our off-moments :)

I suspect there was a USB key drive (4 GB) plugged in (/dev/sdb) - no problem.

Sorry mate, windows is gone from the 60GB drive (/dev/sda).

Also that is an odd partition structure: everything is in a extended partition. That's not a bad thing, per se, just unusual. It may cause problems with dual-booting Win and Ubuntu.

Before installing anything, I would straighten that out. You can use an Ubuntu Live CD, it has the tools to do the partitioning job: Gparted is a GUI tool, there's also the classic command line tool fdisk.

---

### Post by Andavane on 2008-03-29
> **niteshifter said:**
> Hi John,

Don't worry about the error, we all have our off-moments :)

I suspect there was a USB key drive (4 GB) plugged in (/dev/sdb) - no problem.

Sorry mate, windows is gone from the 60GB drive (/dev/sda).

Also that is an odd partition structure: everything is in a extended partition. That's not a bad thing, per se, just unusual. It may cause problems with dual-booting Win and Ubuntu.

Before installing anything, I would straighten that out. You can use an Ubuntu Live CD, it has the tools to do the partitioning job: Gparted is a GUI tool, there's also the classic command line tool fdisk.
Thanks for your words of comfort... I'm quite happy to reinstall again.
Oh, if I may bring in an ancillary issue.
Windows has gone indeed, but I remember that when the laptop was new, the first thing I was urged to do was to take a backup of Windows, onto two DVD's, which I did and I still have the CD's. Looking on them, I see (I think) that there is an 'autorun.exe' and some sony packet files on the first DVD. When I boot into that CD, nothing happens as yet, but...
I was wondering.
Seeing as I have those reinstall CD's, and I won't be needing the laptop for serious stuff for a few months yet, do you think that, whilst the laptop is functioning as a 'toy', I could have a bit of fun partitioning the entire hard drive in a manner which would enable me to reinstall XP Pro, and then dual boot with Ubuntu?
Were that the case, I might open a new thread on that subject, but not if the project would be like flogging a dead donkey.
Just a thought... I value your opinion and am grateful for the help you've given me, and the patience you have shown !   :D

John

---

### Post by nedtoledo on 2008-03-29
^ if that's what you want, I would:
- boot from a windows xp cd
- delete all partitions
- create a 15gb partition and install windows xp on it
- boot from a ubuntu live cd
- create a 15gb / partition
- create a 1 gb swap partition
- create a home partition with the remainder of the hd space
- install ubuntu
hope that helps....

---

### Post by Andavane on 2008-03-29
> **niteshifter said:**
> Hi John,
I suspect there was a USB key drive (4 GB) plugged in (/dev/sdb) - no problem.

.
Not a usb key drive, but I do have a 4GB flash card in the PCMCIA slot.
That must have been what you saw.
Am much impressed how you can tell so much from the lines I sent you.

---

### Post by Andavane on 2008-03-29
> **nedtoledo said:**
> ^ if that's what you want, I would:
- boot from a windows xp cd
- delete all partitions
- create a 15gb partition and install windows xp on it
- boot from a ubuntu live cd
- create a 15gb / partition
- create a 1 gb swap partition
- create a home partition with the remainder of the hd space
- install ubuntu
hope that helps....
Thanks Ned.
From the rap with niteshifter you see my machine didn't come with a CD, but with instructions on making two DVD's. I am wondering whether Windows XP can be restored from those 2 DVD's.
Oh, re the suggestion for a 1 gb swap partition, my RAM I see is 1 gb, so think would suggest making the partition as 2 gb.
Regards
John

---

### Post by niteshifter on 2008-03-30
Hi John,

nedtoledo's scheme is a nice simple one, well worth using.

Some additional thoughts:

For 1 GB RAM, 1GB swap will work. No harm in setting swap to 1.5X or 2X RAM size, for nearly all applications. An exception to that would be something like structure analysis in engineering or mathematically modelling large, complex systems in fine detail. Something to consider: Maybe you wish to add some RAM in the future? Set swap to the max RAM the box can have.

Size is your call, but methinks 15GB for XP could be cramped. I'd try 20GB or 30GB for XP.

A partition for /boot is a handy thing. Doesn't have to be large, 250MB will work nicely. Think of this like hedging a bet: Should the file system get trashed (think hardware malfunction here) there's a better chance of being able to boot if /boot is physically separate than if it's content is distributed among the rest of the physical space hosting said trashed file system. Cheap insurance, in other words.


Here's a scheme that's akin to nedtoledo's with the ideas above incorporated:

1 - Windows, 20 GB
2 - /boot, 250MB
3 - / (20 GB)
4 - Extended
5 - swap (2 GB)
6 - /home (remaining space, approx 17 GB)

I upped the space on / there from personal experience. When I was testing Ubuntu (6.06, 6.10) for my needs (in 2006) /usr alone grew to 16GB - I likes me docs for all this software to be handy. YMMV ;)

---

### Post by Andavane on 2008-03-30
> **niteshifter said:**
> Hi John,

nedtoledo's scheme is a nice simple one, well worth using.

Some additional thoughts:

For 1 GB RAM, 1GB swap will work. No harm in setting swap to 1.5X or 2X RAM size, for nearly all applications. An exception to that would be something like structure analysis in engineering or mathematically modelling large, complex systems in fine detail. Something to consider: Maybe you wish to add some RAM in the future? Set swap to the max RAM the box can have.

Size is your call, but methinks 15GB for XP could be cramped. I'd try 20GB or 30GB for XP.

A partition for /boot is a handy thing. Doesn't have to be large, 250MB will work nicely. Think of this like hedging a bet: Should the file system get trashed (think hardware malfunction here) there's a better chance of being able to boot if /boot is physically separate than if its content is distributed among the rest of the physical space hosting said trashed file system. Cheap insurance, in other words.


Here's a scheme that's akin to nedtoledo's with the ideas above incorporated:

1 - Windows, 20 GB
2 - /boot, 250MB
3 - / (20 GB)
4 - Extended
5 - swap (2 GB)
6 - /home (remaining space, approx 17 GB)

I upped the space on / there from personal experience. When I was testing Ubuntu (6.06, 6.10) for my needs (in 2006) /usr alone grew to 16GB - I likes me docs for all this software to be handy. YMMV ;)

OK will adopt a scheme like this, will set aside one early morning for it.
However I have two doubts:
(1) I seem unable to find "gparted" on the Ubuntu CD; I can see it on my Knoppix CD, but when I went to use it, it asked for my password, which I found weird.
(2) When I had this Sony Vaio laptop new, it came with two partitions on it, the disc being divided into two, if I remember correctly. In the first half there was a (¿secret?) partition which held data for restoring, the remainder of the first half being devoted to Windows XP Pro. The second half had a few data on it, and it recommended that the user put his things there.
It also had some sort of warning about not messing with these partitions, which I ignored.
SO I am wondering whether it might be an idea first to divide the disc into two NTFS partitions to see if the Windows DVD's will restore, and then 'shrink' that partition and follow your plan, or whether to follow your plan and see if the DVD's will restore the XP. They might!
I am a bit worried that I usually think I understand this when reading the posts, but once I've started doing it I get stuck and don't know what to do.

Am confident, however, that if I proceed slowly and surely, some level of understanding will eventually dawn.

So I guess the first step is finding gparted and learning more about that.

Regards and thanks for your help.

John

PS: Re the adding RAM in the future point you made, the machine came with 512 mb RAM, and last year I put in another 512 mb RAM, which is the machine's maximum.

---

### Post by Andavane on 2008-04-01
Don't get me wrong -- I really love this forum. It has taught me so much, and the membership has been just great and  very helpful.

But occasionally I really do seem to stick.
I only wanted to partition my laptop into two equal partitions of NTFS in order try to restore my Windows XP before reinstalling Ubuntu on that.
And yet despite reading umpteen posts and being told that Gparted is on the Ubuntu CD, I just can't find it on there.
And even when I type "GParted" into the post title, I religiously read all the related posts before I make my own, eagerly anticipating that I will find a really simple way to do it.
But I still don't understand what most of them are on about.
yes I can see the screenshots in the psychocats links, but can't get to those menus. I found it on the knoppix CD and then I was asked for a "Password" ! 

It really would be nice to get started on this one.

You know, if there was something which just told you what you had to do: easy peasy Janet and John stuff. It's always easy when someone tells you exactly what to do..

Thanks

John

---

### Post by Duck2006 on 2008-04-01
This is the live cd of gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

This is the documentation of gparted that may help.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by forestpixie on 2008-04-01
gparted is called partition editor and should be in the system >admin menu

---

### Post by Andavane on 2008-04-01
> **forestpixie said:**
> gparted is called partition editor and should be in the system >admin menu
¡ YES !
It is indeed.
(On the live CD of course, not in the installed menu).
That's the step I was looking for.
Regards
John

---

