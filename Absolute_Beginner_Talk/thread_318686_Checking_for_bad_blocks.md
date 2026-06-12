---
title: "Checking for bad blocks"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-14
Hi - I've just upgraded to a larger hard drive so I can give some more room to Ubuntu. I've copied my Windows and Ubuntu partitions to the new drive and I've run bad block checks on the Windows partitions. A couple of bad blocks were found in one of the Windows volumes and re-mapped - so I suppse I'd better check the Ubuntu partition, just to be safe - but how do I do this for a Linux partition?

---

### Post by az on 2006-12-14
sudo badblocks /dev/hda5

If your partition is hda5...

---

### Post by John E on 2006-12-14
Thanks, I'll give that a try.... Incidentally, that raises another question I've been meaning to ask. Is there any easy way (i.e. without a partition manager)) to find out what device is allocated to a given partition? (for example, is it dev/hda1 or dev/hda4?)

---

### Post by John E on 2006-12-14
My god...! I can hardly believe what I've just seen.... '**badblocks**' must surely rank as one of the worst programs ever written...!!

My hard drive's LED flashed continuously for about 15 minutes - but apart from that, the program produced no feedback of any description whatsoever!

No indication that it had started.
No indication of its progress.
No indication when it finished.

For all I know, it might have done absolutely nothing except for flashing that LED...!

---

### Post by mcduck on 2006-12-14
> **John E said:**
> My god...! I can hardly believe what I've just seen.... '**badblocks**' must surely rank as one of the worst programs ever written...!!

My hard drive's LED flashed continuously for about 15 minutes - but apart from that, the program produced no feedback of any description whatsoever!

No indication that it had started.
No indication of its progress.
No indication when it finished.

For all I know, it might have done absolutely nothing except for flashing that LED...!
usually when Linux CLI program doesn't give you any output that means that it has succeeded without any errors..

[QUOTE=badblocks manual]Important note: If the output of badblocks is going to be fed to the e2fsck or mke2fs programs, it is important that the block size is properly specified, since the
       block numbers which are generated are very dependent on the block size in use by the filesystem.  For this reason, it is strongly recommended  that  users  not  run
       badblocks directly, but rather use the -c option of the e2fsck and mke2fs programs.[/QUOTE]

Therefore try 'sudo e2fsck -c /dev/whatever'. Note, that the drive shouldn't be mounted when you do this.

What comes to finding out devices 'sudo fdisk -l' is your friend

---

### Post by John E on 2006-12-14
Thanks, mcduck - I'll give that a try later.

---

### Post by az on 2006-12-14
> **John E said:**
> My god...! I can hardly believe what I've just seen.... '**badblocks**' must surely rank as one of the worst programs ever written...!!

My hard drive's LED flashed continuously for about 15 minutes - but apart from that, the program produced no feedback of any description whatsoever!

No indication that it had started.
No indication of its progress.
No indication when it finished.

For all I know, it might have done absolutely nothing except for flashing that LED...!

My bad.  I should have suggested badblocks -v /dev/hda3

The -v is for verbose mode.

Badblocks can be run as a string of commands.  You can pipe the output of one command to another to do useful things (like feed it into e2fsck).  By default, no output means no problems.

---

### Post by Shatrat on 2006-12-14
> **John E said:**
> My god...! I can hardly believe what I've just seen.... '**badblocks**' must surely rank as one of the worst programs ever written...!!

My hard drive's LED flashed continuously for about 15 minutes - but apart from that, the program produced no feedback of any description whatsoever!

No indication that it had started.
No indication of its progress.
No indication when it finished.

For all I know, it might have done absolutely nothing except for flashing that LED...!

Would you prefer some pop up messages?
"Scanning now!"
"Would you like to Register for Support and Free Money Saving Offers in your Email?"
"Be Sure to visit our online marketplace!"

No news is good news!

---

### Post by moshuptrail on 2006-12-14
Here's a link to my quest for bad block finding.  Read to the end.  Not all the initial advice was good.

[finding bad blocks]("http://ubuntuforums.org/showthread.php?t=309822")

I agree with you on badblocks

[my rant on badblocks]("http://ubuntuforums.org/showthread.php?t=312649")

---

### Post by John E on 2006-12-15
> **Shatrat said:**
> Would you prefer some pop up messages?

[ ... ]

No news is good news!

In my experience - no news usually means the program ain't working properly...! :mrgreen:

---

### Post by John E on 2006-12-15
**moshuptrail** - I just read your horror stories about trying to scan for bad blocks. Jeez - this sort of thing should have been sorted from day 1. I'm amazed that after 20 years on the market, Linux still can't map out bad blocks without screwing up your system!

And why is **badblocks** even bothering to maintain its own bad block list anyway??? For at least the past 15 years, every hard drive ever made has had the ability to maintain its own bad block map. Every manufacturer known now reserves some 'extra blocks' which the drive will map automatically if told to do so. Hasn't anyone wondered why it's so rare for disks to have bad blocks these days? Well, this is why. The disk maintains 'reserved' blocks which get mapped to the bad ones. There's no need for any OS or application to be maintaining a private list of bad blocks (in fact, there hasn't been any such need since the early 1990's). Of course, what this means in practice is that you should be able to scan for bad blocks under Windows and any re-mapped blocks will work for any OS. It's not easy - but that's the way I'm going to do it...!

Right there on my System menu I can select **Administration->Disks**. Surely that would be the sensible place for a disk checking option???

---

### Post by Craftycorner on 2006-12-24
Every once in a while, my system forces a check as I've  a double OS and hop between the two...and a red thingie said I had "non-continuous blocks".  Would some kind soul let me know what that means?  Is that my swap space or is my hard drive about to hit the byte heaven?

:-D

---

### Post by John E on 2006-12-26
I doubt if your system forces a bad block check. Bad blocks are caused by manufacturing deficiencies. Contrary to poular belief, they don't increase with age or usage. This is a misapprehension and is caused by the common observation that disks suddenly start getting lots of bad blocks, just before they die.

What your system is forcing is a check of the file system. It checks, for example, that there aren't 'orphaned' blocks (i.e. blocks which are marked as used but don't belong to any file). It also checks that the same block isn't in use by 2 different files and various other things. 'Non-contiguous' blocks simply means that you have disk fragmentation, which isn't serious.

Back in the old days, you could speed up your disk considerably by defragging it regularly. However, advances in disk cacheing have made this largely unnecessary. Defragging a disk is extremely risky and you shouldn't do it at all unless the disk is very badly fragmented.

---

