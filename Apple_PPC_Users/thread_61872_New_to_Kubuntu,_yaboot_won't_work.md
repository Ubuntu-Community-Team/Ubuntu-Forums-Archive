---
title: "New to Kubuntu, yaboot won't work"
date: 2005-09-02
forum: Apple PPC Users
---

### Post by andydude117 on 2005-09-02
I've been thinking about installing linux for a while, and I didn't know which distro to choose  (And then when I got a Mac, I had like 3 choices).  I heard Ubuntu was like totally easy to use, and I liked using KDE on Knoppix a while back rather than Gnome, so I chose Kubuntu.

Anyway, I just got a 300 gb external hd, and I figured I could partition it and install linux.  So I got to the partition step in the installer, and it took me a while to figure out what I was doing, but I finally got it.   ( I think. )

It looked kinda like this:

#2      1.0 MB    boot
#3      50 GB     ext3
#4      4.7 GB    Swap
#5      45 GB     boot
#6      200 GB   [for use on os x]
#7      200 MB   boot

I don't know why I have three boot partitions, it kept getting to the step where it was supposed to install yaboot, and it said it couldn't, so it said I should go back and make another partition.

But I still couldn't get yaboot to install.  It keeps telling me that that step failed, and I should finish the installation and reboot.  But when I reboot, it goes right back into OS X.

I'm sorry if I sound like an idiot on some kind of drug, but I don't know all these fancy words yet.

Is there a way I could use kubuntu without yaboot?  Or can I install yaboot from OS X?

Thanks,
Andy

---

### Post by DJ_Max on 2005-09-03
Yaboot isn't much more than an interface to OpenFirmware. On boot hold down the 'option' key. It should show OS X and Linux buttons.

If that parition map is right, it's odd. I don't know how or why you have a 4.7GB swap. I've never used an external drive, but I don't know why you have more than one boot paritition.

---

### Post by TroutMaskReplica on 2005-09-04
i have exactly the same problem. it looks like the installation process has a serious design flaw. i searched this forum and there doesn't seem to be a solution.

i just gave up. how much is your time worth?

---

