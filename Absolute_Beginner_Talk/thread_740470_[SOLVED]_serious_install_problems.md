---
title: "[SOLVED] serious install problems"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-03-30
I'm having a serious install problem.  I want to dual boot XP Pro 64 bit and Ubuntu 64 bit.  I have currently a Sata II with the Windows installed.  I have am 80 GB PATA drive I want to use.  I cannot get Ubuntu to load at all, but first some background.

This drive was given to me by a neighbour.  It's basicly new.  It had a windows program called Acronis on it.  I deleted the Acronis partition and the original partiton.  Reformatted it twice.  Stuck it in the machine and it would crash the machine totally.  Acronis wanted to rebuild itself.  I finally ran HDDerase.  It overwrote the whole drive and totally cleared it.  Unplugged my Sata drive and attempted to load Ubuntu.  No soap, kept coming up with HDD loader not present.  I reattatched my SATA drive.  Bios recognized it and I formatted it, and unhooked Sata and tried again.  All I got was a blinking curser on a black screen.  Tried to load 32 bit Ubuntu.  Same thing, blinking curser.  Reattatched Sata and tried to reboot into windows.  Blinking curser again.  Tried messing with the bios.  Changed boot orders and so on, no soap.  It appears the hard drive is dorked again.  Unook it and voila Windows is up again.

I'm going to put the drive back in the old machine and rerun HDDerase again.  I could find no answers in the threads to fit my scenario.  BTW I did use the 32 bit version in a virtual box and got it up and running.  Don't know what happened.  I do remember the drive's header bar was green not blue.  I wonder if I missed something.  It may have been a formatting error.

Any help would be appreciated.  I'll check back in again tomorrow night.  I'm getting tired and have a few things to do before I turn in tonight.

Mark Shuman

---

### Post by dstew on 2008-03-30
With the PATA drive in, can you boot an Ubuntu live CD?

---

### Post by phread59 on 2008-03-30
No I cannot.  I just cannot seem to get the Pata drive to accept Ubuntu.  I just do not know why.  It would be a fresh install on a wiped drive.  I also believe that the 64 bit version may have changed something in the bios.  I had to reset it to the defaults the first time I tried to load it.  May have been a fluke though.  I'm using the download from the Ubuntu server direct to CD.  I do have the 64 bit torrent download on DVD.  The 32 bit had about 6 checksum errors and I did not burn it to dvd.

Mark Shuman

---

### Post by phread59 on 2008-03-31
Bump for the monday morning crowd

Mark Shuman

---

### Post by njparton on 2008-03-31
Does your motherboard BIOS have a boot manager (usually accessed via the esc key)?
 
If so, unplug your SATA drive, use a program such as super F disk to remove the partitions and MBR from the PATA drive, then install ubuntu to it.
 
Plug your SATA drive back in and then use the boot manager in the BIOS to boot between windows and ubuntu.

---

### Post by phread59 on 2008-03-31
NJ the problem is not removal of partitions, there are no partitions.  The drive was unformatted, unpartitioned.  It was wiped totally clean by DDisk erase.  Had to ditch some software that could not be removed (Acronis).  It dorked the drive and would crash the system even after multiple formats.

I believe there was a problem with no partition or formatting. I'm now dumping the unpartitioned new volume on the drive.  I'm going to try to partition it and reformat it.

I plan to leave the windows drive hooked up and install Ubuntu using the disc and changing boot order to cd first.  I saw in a tutorial that I can choose the partiton it goes on.  I will just choose the one from the IDE drive and go from there.

Wish me luck.

Mark Shuman

---

### Post by phread59 on 2008-03-31
Found the stinkin problem I hope.  Found the drive somehow got set to a dynamic disc.  Can't install an op system on one set for dynamic.  Deleted all the volumes on it, reset it to basic, partitioned it and am formatting now.  Seems this is an XP Pro thing.  I'm going to try to load Ubuntu tomorrow night.  Thanks for the help.

Mark Shuman

PS:  Now you know why I'm here,,,,,,,,stinkin windows arghhhh.

---

