---
title: "Xubuntu CD boot gets stuck on empty blue screen"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Eoghanalbar on 2007-04-30
[In the end this problem was solved by using the **alternate install** xubuntu CD]

Very fittingly, it's the same blue as this guy: :confused: 

This problem is on an older dell 2500 inspiron laptop. I am posting this from Xubuntu on another computer running the CD in question, and I checked the checksums anyway.

The laptop used to run windows ME, until I tried to replace it with Damn Small Linux.

This seemed to go off without a hitch until I removed the CD and tried to boot the computer normally. It got past the BIOS screen (that is the right term for that first screen, right?) and the got stuck on a single flashing underscore.

The only way I could get it to do anything was to type in "lowram" and find a combination of options the worked by trial and error, but I still couldn't get it to install to the hard drive.

That's when I tried Xubuntu. Do you know which is more likely: the DSL failure somehow causing the Xubuntu failure (by screwing something up with the HD?), or both failures being caused by a deeper, more fundamental problem?

Is there any more information I could give you, and how could I find it?

Is there any sort of program that I could put on a boot floppy or LD that could somehow "cleanse" the laptop's system, do you know?

---

### Post by oilchangeguy on 2007-04-30
please advise the specs of your machine. and do you have a windows boot floppy?

---

### Post by Eoghanalbar on 2007-04-30
Well, going to "SETUP" by pressing f2 in that thing I'm calling the BIOS screen, I found:

10056 MB HD
system memory 640kB
extended memory 126 MB
 
Is that helpful?

I don't have a windows boot floppy handy, but I could just download that, couldn't I?

---

### Post by Eoghanalbar on 2007-04-30
Oh, by the way this is with the latest version of Xubuntu. I found some hints that an 'alternate installer' might fix the problem, but if there's something else likely, I'd like to try that before I spend five hours downloading it...

---

### Post by oilchangeguy on 2007-04-30
ok, you've got a 10gb hard drive and 128mb of ram. it should run xubuntu. what you can do with the boot floppy is delete the existing partition, create a new one, and format it. in other words start with a blank slate.

---

### Post by Eoghanalbar on 2007-04-30
Okay, I'll go search for a floppy. I'm on windows XP on this computer now, so should I just use that to creat the boot disk?

---

### Post by oilchangeguy on 2007-04-30
ok, go to [www.bootdisk.com](www.bootdisk.com) and create a win 98 boot floppy. do you know how to use the fdisk command?

---

### Post by Eoghanalbar on 2007-04-30
Only very vaguely.

---

### Post by Eoghanalbar on 2007-04-30
Oh wait, is this good: [http://www.bootdisk.com/txtfiles/usefdisk.txt](http://www.bootdisk.com/txtfiles/usefdisk.txt)
?

---

### Post by oilchangeguy on 2007-04-30
set the bios so that the a drive boots first. when the floppy boots select the option to boot w/o cd drive support. then at the a>: type fdisk. follow the prompts until you get to a list of four things. select delete non dos partition, follow the prompts to delete it. then from the list select option 1 to create a new partition. reboot the computer, again select w/o cd support. at the a>: type format c: press enter. answer y to all data will be lost. once format is complete reboot change the bios to boot from the cd drive and try the linux install again.

---

### Post by Eoghanalbar on 2007-04-30
I get: 
"
Remove disks or other media.
Press any key to restart
_
"

(it doesn't restart when I do that, anyway)

Triple checked that the floppy was first in line.

I formatted the floppy before putting the boot disk software on it.

I used "Windows 98 OEM".

---

### Post by Eoghanalbar on 2007-05-01
(Sorry, that was stupid of me. I put the exe on the floppy rather than running it.)

---

### Post by Eoghanalbar on 2007-05-01
Okay, so I finally managed to follow your directions.

However, there was no non-dos to delete, so I just went until there was NOTHING left to delete, then created one new partition to fill all the space, (reboot), fomatted it, (reboot), then tried to start up xubuntu.

Same problem!

Could I possibly have used the wrong kind of partition or something?

---

### Post by Eoghanalbar on 2007-05-06
In the end I solved this problem by using the xubuntu alternate install.
Thank you for your help anyway, oilchangeguy, although I doubt you'll read this.

---

