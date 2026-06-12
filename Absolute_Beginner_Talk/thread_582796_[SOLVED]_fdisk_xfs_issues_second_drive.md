---
title: "[SOLVED] fdisk xfs issues second drive"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-10-20
After a couple of hours googling this, I'm fairly sure I'm in way over my head. My Ubuntu Feisty is running nicely and I don't want to mess it up.

I'm working my way through the fantastic tutorial on [setting up MythTV]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O") and came up on using the xfs file system for recordings. That's when the wheels came off. I moved whatever data off my second drive, deleted the one partition I had on it, and went to create an xfs one, but the option for that in gpart is disabled. So I read that I need to use fdisk to create that partition with the xfs file system, but that is where I get a little lost.

Could someone direct me to a tutorial on this subject? Once I get the partition created, mounted, and be able to read/write files to it, I can continue with the MythTV guide.

Thanks! I'm going to go make another pot of coffee. It's been a long night, and I'm sure I'll see the sunrise before I'm recording TV on this machine. ](*,)

---

### Post by JBAlaska on 2007-10-20
You need to boot from a LiveCD to use gparted. Maybe you could unmount your second HD, but booting from the LiveCD is probably the easiest.

I'm using JFS on my MythTV box and it works very well. On my next Myth box I'm going to try XFS.

---

### Post by Hopworks on 2007-10-20
I couldn't find my LiveCD (Ubuntu Feisty Server 7.04) nor the iso, so I downloaded it again, burned it, and then while I was waiting, I happened upon GParted LiveCD. Hmmm. Which did you mean JBAlaska? I'm guessing the GParted LiveCD since it seems geared towards exactly what I want to do.

Also, is there anything else I need to do once I get that xfs partition created?

And finally, you said you used JFS on your MythTV box. Should I be looking at that file system instead? I know nothing of either files systems, except there seems to be a little debate on the better of the (ext3 verses xfs) as far as performance and reliability.

Thanks for the speedy reply! It's nice to know I'm not the only soul burning the midnight oil.

Hop

---

### Post by Hopworks on 2007-10-20
OK, booted with the GParted LiveCD and went to that drive (it was blank, no partitions), tried to create an XFS partition, and the option was available. It didn't work though when I applied, and I thought I saved the details to root, but the file is nowhere to be found.

I'll do it again, and make sure I save that file to a known place in the file system, or at least write down the problem. something about the drive being busy, or...

Hop

---

### Post by Hopworks on 2007-10-20
Alright, just tried it again, this time I wrote it down, because when I try to save the results, it seems to go nowhere.
Cannot open /dev/sdb1 Device or Resource Busy. :confused:

Hop

EDIT: OK, I'll try the Feisty LiveCD this time. Maybe moving the drive's IDE connection physically might help also. Who knows. At this point, my ignorance on this subject will cost me lots of time. Not with setting up MythTV, the tutorial is excellent. Just setting up XFS.
Oh, and JFS didn't work either.

---

### Post by Hopworks on 2007-10-20
I thought I had it. I used the Ubuntu Server 7.04 LiveCD and was able to create an XFS partition. Then, when I boot, I go to look at it in GParted, and I have a warning triangle with an exclamation point in the middle. 

The warning says "Unable to read the contents of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

WHAT?

I didn't know that XFS was something I had to install. I thought it was part of linux or maybe Ubuntu. Can someone help me with this? Like an idiot, I did apt-get install xfs and installed a font server. ](*,)

I'm going to catch a few hours sleep. I'm almost in a coma at the moment, and could do more harm than good.

Hop :confused:

---

### Post by JBAlaska on 2007-10-20
Are you trying to use xfs for your root? 
The way I have mine setup is as follows:
/ (root) ext3
/video JFS
/swap

My /video partition is not the default so I had to tinker with myth.

If your using Mythbuntu It's better if you follow the standard storage locations (/var/lib/), then samba and nfs get preconfigured for you.

---

### Post by Hopworks on 2007-10-20
> **JBAlaska said:**
> Are you trying to use xfs for your root? 
The way I have mine setup is as follows:
/ (root) ext3
/video JFS
/swap

My /video partition is not the default so I had to tinker with myth.

If your using Mythbuntu It's better if you follow the standard storage locations (/var/lib/), then samba and nfs get preconfigured for you.I hope I understand your question correctly.
I have a second drive that was blank, now has one XFS partition, that's it. The other drive, or /dev/sda has my filesystem, set to ext3. Now I'm getting ```
fdisk -l /dev/sdb

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```which is different than before, so I did something wrong. >sigh<

I found my problem earlier, I didn't have the xfsprogs installed. I have that done, so I guess I should just start over.

What I want to end up with is the second drive partitioned xfs, and mounted to /mythtv. Of the many web pages I read through, one in particular [filesystem implementor's guide, Part 10]("http://www.ibm.com/developerworks/library/l-fs10.html") tells of tweaking the mkfs.xfs options to maximize performance, like setting the size of the metadata journal, number of allocation groups. I don't know anything about that, and I want to do it right so I can squeeze as much performance out of mythtv as I can.

I know there are mythbuntu installs, but I want to keep my current install, all the work I did on my LAMP, settings, as I stumble through the process of learning Linux Ubuntu.

---

### Post by kerry_s on 2007-10-20
> **Hopworks said:**
> I thought I had it. I used the Ubuntu Server 7.04 LiveCD and was able to create an XFS partition. Then, when I boot, I go to look at it in GParted, and I have a warning triangle with an exclamation point in the middle. 

The warning says "Unable to read the contents of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

WHAT?

I didn't know that XFS was something I had to install. I thought it was part of linux or maybe Ubuntu. Can someone help me with this? Like an idiot, I did apt-get install xfs and installed a font server. ](*,)

I'm going to catch a few hours sleep. I'm almost in a coma at the moment, and could do more harm than good.

Hop :confused:

**apt-get install xfsprogs**

is the 1 your looking for.

---

### Post by Hopworks on 2007-10-20
> **kerry_s said:**
> **apt-get install xfsprogs**

is the 1 your looking for.Thanks for that. I actually found that out myself before my three hour nap, and felt pretty stupid for not seeing that sooner.

Where I am at now is 
[LIST=1]
[*]I unmounted my previous mistake.
[*]Used fdisk /dev/sdb and got a warning about the partition table, will fix on write, so I did that, and the drive was ready again.
[*]Did fdisk /dev/sdb again and created a primary partition the size of the drive.
[*]Used mkfs.xfs -L video /dev/sdb and it returned
[/LIST]```
meta-data=/dev/sdb1              isize=256    agcount=16, agsize=1831535 blks
         =                       sectsz=512   attr=0
data     =                       bsize=4096   blocks=29304560, imaxpct=25
         =                       sunit=0      swidth=0 blks, unwritten=1
naming   =version 2              bsize=4096
log      =internal log           bsize=4096   blocks=14308, version=1
         =                       sectsz=512   sunit=0 blks
realtime =none                   extsz=4096   blocks=0, rtextents=0

```

Now I'm ready to mount it via 'mount', and reading the man page on mount at the moment. Am I on the right track?

---

### Post by Hopworks on 2007-10-20
I think I finally got it. Now that I know a bit more than I did going in, I finally mounted the XFS partition without incident, and it appeared in my media folder where I wanted it mounted. WHEW.  I almost missed the mkdir step. I'll be spending an hour writing all this down for future reference because I don't want to go through that hell again.

Only problem I have now is that I can't write anything to that folder. I brushed across a lot of threads about setting the ownership, permissions, setting all that up in fstab. I got to make sure MythTV can access it of course.

Thanks to those that helped me along. It was aggravating, but was also fun to learn and earn all this new knowledge.

Hop

EDIT: Just chowned the folder to username:mythtv and now I can read and write files to it. Finally success! Now on with the MythTV setup guide.8)

---

