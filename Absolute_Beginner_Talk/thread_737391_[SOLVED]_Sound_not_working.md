---
title: "[SOLVED] Sound not working"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Paul271 on 2008-03-27
Hi I am new to ubuntu 7.10 I have installed it on a  ASUS notebook M51SN I have no sound.
description: Audio device 
       product: 82801H (ICH8 Family) HD Audio Controller 
       vendor: Intel Corporation 
       physical id: 1b 
       bus info: pci@0000:00:1b.0 
       version: 03 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel 
I am new to Linux I hope some one can help.

---

### Post by balaknair on 2008-03-27
Hello Paul271
The easiest way to fix sound issues for your sound card(ICH8 family) is to upgrade your kernel
I'm assuming you're running the 32-bit version of Ubuntu.
To do this, you have to enable the Gutsy (Ubuntu 7.10) Backports repositories in Software Sources.
System Menu> Administration> Software Sources---> Updates>Gutsy Backports(enable this option)
Then open a terminal window(Applications> Accessories> Terminal) and paste this command

sudo apt-get install linux-backports-modules-generic

Restart the system, and make sure all volume channels are unmuted(they are muted by default) by clicking on the Speaker icon in the top panel near the right upper corner.

PS: if this fixes your problem please reply and mark this thread as solved.
Thanks and good luck.

---

### Post by Paul271 on 2008-03-27
Sound still not working.

---

### Post by balaknair on 2008-03-27
OK then, I think you might need to upgrade to ALSA 1.0.16
I've described the steps here:
[http://ubuntuforums.org/showpost.php?p=4512734&postcount=4](http://ubuntuforums.org/showpost.php?p=4512734&postcount=4)

An easier method is described here, but I've never tried this one, so I can't say for sure.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

(I'm sorry, I'd really like to help you with specific step by step instructions, but it's 2:30 AM here and I've got to get to work in the morning; I'm up putting the finishing touches on a paper I have to submit for review today. But I will check back tomorrow evening for sure(GMT +5:30))
All the best

---

### Post by superprash2003 on 2008-03-28
also give this a shot [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by NarahariBabu on 2008-03-28
Hello balaknair,

Thank You very much for the excellent & easiest method. It worked on my Dell Laptop. Now I am able to hear Songs & watch Movies.

Thanks Again.

Cheers
NarahariBabu

---

### Post by NarahariBabu on 2008-03-28
BTW How do I thank balaknair and mark this thread as solved

Cheers

---

### Post by balaknair on 2008-03-28
> **NarahariBabu said:**
> BTW How do I thank balaknair and mark this thread as solved

Cheers
@NarahariBabu: Glad to know your problem has been solved.
-In order to mark the thread as solved, I think you have to be the one who created the thread.
-In order to thank someone, click on the little medal in the bottom right corner of the post you want to thank.
PS: please don't thank me, it's my pleasure to have been able to help you. If you do want to thank me, I think the best way would be to pay it forward and help someone else in turn, either within Ubuntuforums or elsewhere.

---

### Post by Stvnx7 on 2008-03-31
Enablign the back reposetories and restarting cleared the problem. Thank you very much for this balaknair.

---

