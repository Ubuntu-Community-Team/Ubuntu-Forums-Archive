---
title: "Defragmenter?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by AliL on 2007-09-17
I know Ubuntu automatically defragments your files like OSX does, but I have a slight problem that this can't fix.

I'm currently dual booting with XP and although I'm ashamed to say it I use XP more simply because whenever I'm using the computer I'm in a rush and I know how windows works better but enough of my trying to defend a weaker OS...

Basically, on the XP partition there are some corrupt sectors (I think the hard drive may be dying as the computer is a 4 year old laptop that gets lots of abuse) and one of these corrupt sectors has found it's way into the boot area so I now cannot boot into XP, not even in safe mode. Is there a defragmenter that could fix this problem (I know the windows program PerfectDisk 8 can do something like this but I need to get into windows to use it - catch 22). So is there a program or am I gonna have to do a botched operation and run this program through WINE? Also the windows partition is NTFS to further add to the problems.


Many thanks for any help.

AliL

---

### Post by oilchangeguy on 2007-09-17
even if you could defrag windows, this will not cure your problem. boot from your windows cd, and enter the repair console. at the c: prompt type chkdsk /r and press enter.

---

### Post by macogw on 2007-09-17
I don't think defragging fixes corrupt files.  It just moves things around toward the front of the drive.  You might need to reinstall Windows.

---

### Post by oilchangeguy on 2007-09-17
> **macogw said:**
> I don't think defragging fixes corrupt files.  It just moves things around toward the front of the drive.  You might need to reinstall Windows.

please explain how reinstalling windows will fix a dying hard drive?

---

### Post by AliL on 2007-09-17
Well the thing is I want it to blacklist these sectors so that files are not put on them which is an option in PerfectDisk.

@ oilchangeguy - I'll have a go with running the chkdisk util and report back when it's done.

---

### Post by yabbadabbadont on 2007-09-17
Edit: Never mind.  I misread the first post.

---

### Post by Shazaam on 2007-09-17
It scans the drive for errors (chkdsk) during install and gives you the option to repair or flag the bad sectors. As long as there aren't too many.:)
Better thing to do is buy a new drive and clone the old one.

---

### Post by poe503 on 2007-09-17
My experience with bad sectors is that the hard drive is going south.  Back up your files and shop for a new drive.

---

### Post by AliL on 2007-09-18
Well I've run chkdsk on the windows partition and it takes ages and gets stuck at some bits for a while and makes the same odd noise that it does when it can't read a sector but then moves on again. I ran the utiltity 4 times and every time the windows partition wouldn't reboot...The odd thing is that I'm running Ubuntu on the computer. I guess ubuntu has better bad sector management than windows...what a surprise...

So how would I find out whether the HDD is IDE or SATA, will all HDDs of the correct type be compatible or will I have to find the max limit my laptop can take?

Also how do I clone the drive?

---

### Post by LowSky on 2007-09-18
take the drive out and look at it... mini IDE has a bunch of pins on the hard drive, SATA is just a socket like on the desktop version .. being 4 years old its most likely 2.5" IDE Hard drive

size limit doesnt matter buy what ever you can fit

---

### Post by asmoore82 on 2007-09-18
> **AliL said:**
> I know Ubuntu automatically defragments your files like OSX does, but I have a slight problem that this can't fix.

That's actually not true; the difference is subtle but important...

GNU/Linux systems (or filesystems, to be precise) simply do not need to be defragmented.
It is not that they do it automatically; rather it is simply not necessary.

---

### Post by yabbadabbadont on 2007-09-18
Actually, *that* is not quite the whole story either.  :D

They do get fragmented.  It is just that you generally won't notice a performance hit until it becomes severely fragmented.  At which time the normal procedure is to backup the filesystem, recreate it, then restore from the backup.

---

### Post by stchman on 2007-09-18
> **AliL said:**
> I know Ubuntu automatically defragments your files like OSX does, but I have a slight problem that this can't fix.

I'm currently dual booting with XP and although I'm ashamed to say it I use XP more simply because whenever I'm using the computer I'm in a rush and I know how windows works better but enough of my trying to defend a weaker OS...

Basically, on the XP partition there are some corrupt sectors (I think the hard drive may be dying as the computer is a 4 year old laptop that gets lots of abuse) and one of these corrupt sectors has found it's way into the boot area so I now cannot boot into XP, not even in safe mode. Is there a defragmenter that could fix this problem (I know the windows program PerfectDisk 8 can do something like this but I need to get into windows to use it - catch 22). So is there a program or am I gonna have to do a botched operation and run this program through WINE? Also the windows partition is NTFS to further add to the problems.


Many thanks for any help.

AliL

1.  Sounds like your hdd is about to cr@p out.  I would back up everything while you can.

2.  Linux is different.  You need to keep using it to get the hang of it.

---

### Post by asmoore82 on 2007-09-18
> **yabbadabbadont said:**
> Actually, *that* is not quite the whole story either.  :D
you are correct there; I have not yet laid open the whole truth.
> **yabbadabbadont said:**
> They do get fragmented.
Wrong.
There is no "fragmentation" *as windoze refugees know it*.
While files can be **non-contiguous**, there is no filesystem [entropy]("http://en.wiktionary.org/wiki/Entropy") and
**there is no discernable "performance hit"**. 
> **yabbadabbadont said:**
> It is just that you generally won't notice a performance hit until it becomes severely fragmented.
as just mentioned; **there is no discernable "performance hit"**,
this is **especially** true on modern multi-tasking operating systems with caching mechanisms.
And it is virtually **impossible** for filesystems to become "severely" **non-contiguous**
unless they have done many operations while 95-100% full.
> **yabbadabbadont said:**
> At which time the normal procedure is to
backup the filesystem, recreate it, then restore from the backup.
Totally wrong; while *that* may be "normal" in some circles, it does very little
in the way of making it necessary "procedure." Even if you are somehow threatened
by the existence of **non-contiguous** files in your filesystem, you would *never*
need to "recreate" the filesystem. The most you would have to do, if you were so inclined,
would be to move[copy and delete] the files to another location, and then move them
back again to the very same filesystem: after the move away and back again, they are,
in truth, completely different files with the exact same data; and the space freed by moving
them away decreases the chances of their replacement files being **non-contiguous**.

The point of all of this way to specific information is this:
Windoze "power users" are accustomed to dealing with the shortcomings and design flaws
of their OS and I am not.

More specifically, there are 2 universal truths hiding in the margins here:
Number 1: if you do not defrag Windows 9x, it WILL choke to death on its own blood.
Number 2: [Big Suprise], [Linux is NOT Windows 9x]("http://linux.oneandoneis2.org/LNW.htm")

P.S. do not be confused by google searching and seeing articles proclaiming the
horror of "linux fragmentation." They are referring to the **co-existence** of
100s of distros and are not in reference to the filesystem.

---

### Post by yabbadabbadont on 2007-09-19
Believe what you will, I don't care to try to change your mind.  However, I have been using linux on my machines for the past 11 years, and have found the behavior to be different than what you describe.  As with all things, your mileage may vary.  ;)

---

### Post by MerlinX420 on 2007-09-19
From what i know about how a hard drive stores and writes data every hd no matter what the OS is would eventually develop bad sectors. I don't know about the fragmentation of files thou. it seem that Linux does a better job at keeping the files in line so to say. Like you said the laptop was abused and might have been dropped during a read that damaged the platters. The age of the machine is irrelevant. I'm running a 10 year old machine with the original hd. It still runs like a top. 20 times better since I installed ubuntu.

---

### Post by AliL on 2007-09-19
OK OK, I didn't want to start off a row about what happens with fragmentation and whether it happens or not, so everyone just take a chill pill...phew...

So I gather my HDD is about to die, so what is the simplest way of backing all my files up? I have ubuntu running on the dying machine, XP running on another machine (I can't put ubuntu on it coz my dad reckons it'll break it) and a huge 500GB external hard drive to which I can back my files onto temporarily.

Is there a free utility out there for ubuntu or XP which I can use to do this or is it a case of "cut and paste" the files from one HDD to another? Because I'd like to keep my programs and settings for XP on the dying machine the same and copy and paste won't do all this I'm sure because it'll kill the registry and whatnot...

P.S. Don't start another war if I'm wrong about the registry thing or something else, all I want is a solution...lol...

thanks in advance, it's much appreciated

AliL

---

### Post by asmoore82 on 2007-09-19
> **yabbadabbadont said:**
> Believe what you will, I don't care to try to change your mind.  However, I have been using linux on my machines for the past 11 years, and have found the behavior to be different than what you describe.  As with all things, your mileage may vary.  ;)

this question has been asked before; and maybe you replied in that old thread...

but what *% non-contiguous* do you consider to be unacceptable??

---

### Post by Graham Power on 2007-09-19
good day all 
you can try this . find Norton Ghost.exe that can be put on a bootable cd rom install new harddrive into the computer . Ghost the image of the old HD to new one . when finished turn off computer remove old hd and put new one in same place . Reboot and cross figures that you have your old system back to normal. 
sorry that this is not a linux solution and using a norton product but it worked for me 
good luck

---

### Post by AliL on 2007-09-19
> **Graham Power said:**
> good day all 
 find Norton Ghost.exe

Isn't that a copyrighted product that I'd have to pay for? Or are you suggesting that I download it illegally? How very dare you...:P

---

### Post by Graham Power on 2007-09-19
Just thought of another way .
you may have to verify that it will work 
If you have the ubuntu live cd boot into it instead of norton ghost .There must be some tools in there that can image a drive. too new to know myself

---

### Post by asmoore82 on 2007-09-19
if you need to back up files, just copy them over with any LiveCD.
if you want to back up a whole OS; I recommend [clonezilla]("http://clonezilla.sf.net/").

---

### Post by yabbadabbadont on 2007-09-19
> **asmoore82 said:**
> this question has been asked before; and maybe you replied in that old thread...

but what *% non-contiguous* do you consider to be unacceptable??

When it gets to the point that I start noticing a slowdown.  Not an objective measure, I admit.  It should be noted that it only becomes an issue on filesystems with a **lot** of write/replace activity.  I don't worry about it on filesystems that rarely change as it doesn't seem to affect the speed of reads enough to be noticeable.

---

### Post by Ant_Merlin on 2007-09-19
I agree with Asmoore82,  clonezilla would do the trick as long as you have CD/DVD Writer to burn the ISO image. Don`t use Norton ghost as you could screw up the Ext3 partitions. If you dont have a writer then you could always create a backup of Ubuntu using Tar.
This clever guy show you how...
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

Ant.

---

### Post by tombott on 2007-09-19
> **AliL said:**
> OK OK, I didn't want to start off a row about what happens with fragmentation and whether it happens or not, so everyone just take a chill pill...phew...

So I gather my HDD is about to die, so what is the simplest way of backing all my files up? I have ubuntu running on the dying machine, XP running on another machine (I can't put ubuntu on it coz my dad reckons it'll break it) and a huge 500GB external hard drive to which I can back my files onto temporarily.

Is there a free utility out there for ubuntu or XP which I can use to do this or is it a case of "cut and paste" the files from one HDD to another? Because I'd like to keep my programs and settings for XP on the dying machine the same and copy and paste won't do all this I'm sure because it'll kill the registry and whatnot...

P.S. Don't start another war if I'm wrong about the registry thing or something else, all I want is a solution...lol...

thanks in advance, it's much appreciated

AliL

As previously mentioned Ghost would do this for you, and I have done this myself with Ubuntu installs many a time with no problems with the ext3 file system becoming corrupt.

You have an external HD so you can ghost the image of your laptop to that.

You need a Bootable CD with Ghost on it to do this.

I recommend you google hiren boot cd and download an iso of it,

Boot from it in your laptop with the external HD attached.

And goto the drive imaging section, all should become clear from there.
PM me if you want more info.

---

### Post by AliL on 2007-09-20
Right then, I've just ordered a nice shiny new HDD from eBuyer ([clicky]("http://www.ebuyer.com/UK/product/130338/rb/0")) and it should be with me this time next week (gotta love the free delivery...).
Until then there's not much I can really do so I'll post back when I've got it and having a go at doing it...

---

### Post by AliL on 2007-09-23
Right then, I've copied the important files across to my external HDD, but I want to be sure that the files have copied across Ok, so I wanted to do some MD5 checksum checks to make sure none of the files are corrupt.

So is there a way of creating an MD5 checksum for a folder and all of the files and folders inside it? Or will I have to create a zipped file to do this? And if I do, what's the command?

---

### Post by AliL on 2007-09-24
Sorry for the bump, but does anyone know if I can get an md5 checksum of a directory and all of the files and folders within it, or even a batch of checksums exported to a file, which can then easily be checked against the files I've copied across?

---

### Post by AliL on 2007-09-27
deleted

---

