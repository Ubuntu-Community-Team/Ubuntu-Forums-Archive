---
title: "Best Way to Recover Data?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-10-26
First off, I'd like to say, What the Hell? Why did the CD erase my HDD, when I explicitly asked it to go into GParted?

Second, I've got an issue. See above for the short story. I have no idea what happened.... I click to open GParted and the next thing I know, my hard drive's buzzing and the partitions are fried off the face of existence. Again, What. The. Hell?

Before I go any farther, I'd like to know whether there's a way to restore the drive. There used to be 7 partitions, now there're none. I swear to God, I did nothing except click to open Gparted. 

One last thing, guys: please don't try to say that I didn't click the Gparted icon by mistake or something along those lines. I would like either explanations or solutions to recovering my data. I type this off a LiveCD, so the hard drive itself is untouched.

"sudo fdisk -l" reports nothing. If there are any other commands I should run to check, please give those also. 

Also: Thank the Gods above for backups. I only have a 1/3 of my total stuff, but that's that much less I'll need to worry about. I hope. 

Thanks for any and all help!

---

### Post by oilchangeguy on 2007-10-26
try this:
[http://www.rescubuntu.info/node/1](http://www.rescubuntu.info/node/1)

---

### Post by Happy_Man on 2007-10-26
It looks wonderful, but where would I put it? The HDD is naturally out of the question... and I don't have enough RAM to store it in this live session.

---

### Post by e_james on 2007-10-26
You don't say, but I assume you have assured yourself that the data loss is not an illusion caused by a glitch in the live CD.

---

### Post by Happy_Man on 2007-10-26
No, I booted a Linux Mint CD to check that, it's blank there too. Also, GRUB gives the ominous error 22.... I'm pretty sure this is legit. :(

---

### Post by Happy_Man on 2007-10-26
Bumping it up as a last hope.... if nobody responds by morning for me, then I'll just go ahead and repartition. Please, someone, help me out!

---

### Post by evilregis on 2007-10-26
Do you have a spare HD from an older machine?  You could pop that into the computer (as a master, keeping your existing borked drive as a slave), install an OS there and see what sort of recovery you can get out of it.

I've never had to do anything like this in Linux, but I've had to go and do a handful of failing drive backups and that's how I would go about rescuing what I could.

Good luck.

---

### Post by MegaJim on 2007-10-26
I've never used it but Parted Magic seems like it could do the trick.

Its founded by the same guy who made GParted Live, so expect it to be of a high quality, check out the feature list:

[http://partedmagic.com/programs.html](http://partedmagic.com/programs.html)

of note at the bottom: TestDisk	-	partition scanner and disk recovery tool

website of TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Happy_Man on 2007-10-26
@evilregis:

No, unfortunately, I do not. As I said, though, I have all the important stuff backed up, so this is mainly an intellectual exercise. Sorry if that wasn't clear.

@MegaJim:

Yeah, I've used the Gparted LiveCD before (unfortunately i don't have a copy on me ATM) so Parted Magic would be my best shot. As I said, though: Where would I put it? I don't want to foul the HDD, and I doubt I have enough memory to burn a CD without a swap partition handy, which would require me to write on my HDD, but I can't, etc. It's a catch-22.

---

### Post by Can+~ on 2007-10-26
I feel your partition tables were.. somehow dropped.

According to wikipedia:

> When a partition is deleted, in general, only its partition table entry is removed from a table; and although the data is no longer accessible, it still remains on the disk until being overwritten. Specialized recovery utilities, (such as TestDisk and gpart), can locate lost file systems and recreate a partition table which includes entries for these recovered file systems

How were the partitions distributed before this happened?

---

### Post by MegaJim on 2007-10-26
Parted Magic is 35 mb in weight

You could also try downloading TestDisk from their site and running it on live-cd

---

### Post by e_james on 2007-10-27
I believe that partition recovery software scans the drive looking for the indicators for partition start and end. If deleted partitions are treated similarly to deleted files, it may be that the partition table still contains all the necessary details. You just need to reset the value that is currently saying "no partition" using a disk editor. Grub error 22 implies that Grub is still present.

---

### Post by Happy_Man on 2007-10-27
Hmmm.... interesting. Looking through, it seems Can+~ and e_james were right; the table was just screwed up. I went ahead and wiped it anyway, I've been looking for an excuse to do so for a long time now. On the plus side, I now have a GParted LiveCD and a whole list of amazing utilities for HDD recovery. Thanks, everyone!

---

