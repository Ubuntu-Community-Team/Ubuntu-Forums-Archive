---
title: "Getting Rid of Windows Partition"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jmusso on 2007-06-30
Okay, so I know I've been making many-a-noobish thread around here lately... But I think this is the last of them (for a bit anyway). 

I'm running a dual boot on my interal 80gb HD with Feisty Fawn and XP Home. I gave Ubuntu about 10gb or so (after much grief getting it to partition correctly), but now I want to just run Ubuntu and kick XP off. Firstly I'm going to transfer all my mp3's and files I want to keep and such onto an external HD that I've formatted with a lot of ext3 space (I'll install the fs-driver into windows so I can write to it). My question now is this: How do I clear out the Windows partition (there's also a 10gb or so Recovery partition) and attach it to the Ubuntu partition on my internal drive...? Thanks much.

---

### Post by Nikron on 2007-06-30
> **jmusso said:**
> Okay, so I know I've been making many-a-noobish thread around here lately... But I think this is the last of them (for a bit anyway). 

I'm running a dual boot on my interal 80gb HD with Feisty Fawn and XP Home. I gave Ubuntu about 10gb or so (after much grief getting it to partition correctly), but now I want to just run Ubuntu and kick XP off. Firstly I'm going to transfer all my mp3's and files I want to keep and such onto an external HD that I've formatted with a lot of ext3 space (I'll install the fs-driver into windows so I can write to it). My question now is this: How do I clear out the Windows partition (there's also a 10gb or so Recovery partition) and attach it to the Ubuntu partition on my internal drive...? Thanks much.

Well.  You probably (easily) do this while running the feisty install, but the easiest way would be to burn an iso of  [gparted]("http://gparted.sourceforge.net/"), and booting off of it.  It should be very evident of what to do when you get there.  (You'll slide a few boxes, delete a few, easy stuff =)

---

### Post by hyper_ch on 2007-06-30
and before you touch any partitions make sure you have a backup of your data. Although chances are slim that gparted somehow f***** up your ext3 partitions it can happen...

---

### Post by cotcot on 2007-06-30
Take the Gparted liveCD from the link in previous post.
And also again backup (to your external hdd) before you move partitions. If you have a 32 bit system partimage from a liveCD can help you. For 32 and 64 bit the use of "tar" is possible as well. [Here]("http://www.debianhelp.co.uk/tarbackup.htm") is an instruction for "tar" and [here]("http://www.digitalissues.co.uk/html/os/misc/partimage.html") is a link to partimages docs. Partimage is something like Ghost in windows.

---

