---
title: "Blank Screen in Alternate Install"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Bob042 on 2006-07-13
I've been told to try the alternate install disc to get Ubuntu working, because the LiveCD wasn't working. Now, I can get the installer working, it goes through Language, keyboard, network (doesn't work with my wireless, but I kind of expected that), and then it gets to the partitioning. The problem is, after the load bar "starting partitioner" comes up and goes away, the installer just sits there with a blank screen, I've left it for 15 minutes. Any ideas on what the issue is?

---

### Post by Bob042 on 2006-07-13
A bit of an update to this: If I press control+C, which I saw somewhere else, it moves on, but doesn't make sense. It says something like "here are the partitions", but it doesn't list partitions. The first two options, RAID and something else, say they'll finalize the partition. Guided partitioning doesn't do anyhting, another blank screen. Partitioning help gives help, but nothing really useful. The last option is to continue with these settings, but I haven't made any settings.

---

### Post by bikeboy on 2006-07-13
Can't remember if the alternate installer has a "safe video" option but if it does I suggest you try it. Particularly for ati cards.

---

### Post by Bob042 on 2006-07-13
I think I may have phrased my statement wrong. The screen isn't blank, so much as blue. The problem is the installer is stalled, not my video. By the way, I have a Nvidia 6600Gt, if that makes a difference.

---

### Post by taurus on 2006-07-13
Are you using RAID on your system?

---

### Post by Bob042 on 2006-07-13
No. I have one SATA hard drive, and 2 IDE CD drives, one being a burner, and one an old one I threw in to see if it would get rid of install errors.

---

### Post by Bob042 on 2006-07-14
Still trying to get this figured out...

---

### Post by bikeboy on 2006-07-15
Maybe try going using some advanced boot options when you start the installer. From memory, when the cd loads it gives you some options and you can press F6 for advanced. Not sure though, don't have an alt cd on hand.

If you can do that, at the end of the command line that comes up try adding noapic nolapic.

---

### Post by Thorndeux on 2006-07-15
Just wanted to say that I did not encounter problems with the same video card (Nvidia 6600 GT), so that shouldn't be the issue.

---

