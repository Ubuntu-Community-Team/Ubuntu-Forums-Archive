---
title: "Super beginer questions about dual booting off of 2 SATA hard drives"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ekosz on 2007-04-23
I have been been interested in Ubuntu for a couple months now and am finally ready to take the plung, but first I want to make sure I know what I am doing first... so that I don't crash my system (its brand new :P)

My Build:
AMD AthlonT64 X2 4200+ Dual-Core - CPU
GigaByte GA-M55SLI-S4 nForce4 SLI chipset - Motherboard
1024MB - RAM
NVIDIA GeForce 8800GTS 640MB - Video Card
and then the tricky part.. two 250GB SATA hard drives

I was wondering how I should install Ubuntu 7.04 on my system so I can dual boot comfortably.  

What I would like to be able to work-
I was wonder if it was possible (and then how to achieve this) to have Windows on one hard drive fully (all 250gb) and then the second hard drive having Ubuntu installed which would take up 100gb then the other 150 being shared between the two.  How should I partition the second hard drive?  A 2gb swap, 3gb root (/), and then like a  95bg /home and finally a 150 FAT32?  Would that work?  

Currently Windows is installed on the first drive and the second is pre-formated as NTFS (but I can change this yes?

Is there a picticlar order that I should place the partitions?  Also I heard you should sometime put the swap on the other hard drive (the first one) so that the HD doesn't have to read and write the same HD at the same time. Is this true?  Also what should I use to partition the hard drive?  Would the built in partitioner work that comes with the Live Disc?

Sorry for so many questions.  I think I got this down but I want to make sure I am right before I proceed any further.

Thank you all for helping!

P.S. Last time i trying putting a older version Live Disc into this build I got this error [http://ubuntuforums.org/showthread.php?t=359034](http://ubuntuforums.org/showthread.php?t=359034) .  Do you think the new version would have fixed this?

---

### Post by antoz on 2007-04-23
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by indytim on 2007-04-23
Another good guide can be found at:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0]("http://kubuntuforums.net/forums/index.php?topic=3081671.0")

IndyTim

---

### Post by ekosz on 2007-04-23
That first site was really good, but only talked about if there was one hard drive.  And the one he linked to that talked about multiple hard drives only talk of IDE HDs.  Anyone know if I should just partition one hard drive then use the second one as a shared data source?

---

### Post by jfinkels on 2007-04-23
> **ekosz said:**
> That first site was really good, but only talked about if there was one hard drive.  And the one he linked to that talked about multiple hard drives only talk of IDE HDs.  Anyone know if I should just partition one hard drive then use the second one as a shared data source?

You can partition your drives in whatever way you want, really. You would be perfectly fine doing one hard drive Ubuntu + swap and one hard drive Windows.

---

### Post by antoz on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

The above link talks about multiple drive install. I doen't really matter which way you go Ubuntu is quite happy on a other Hardrive depending on where grub gets installed though I think you may have to change the boot squence in the bios so that it boots first.
I myself have both windows and Ubuntu on one drive. I am not really experienced enough to give you tecnical advice but I hope this helps.
I have 2 sata drives 250gig and 200gig

---

