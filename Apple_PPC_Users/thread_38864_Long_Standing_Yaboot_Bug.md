---
title: "Long Standing Yaboot Bug"
date: 2005-06-02
forum: Apple PPC Users
---

### Post by joey on 2005-06-02
Howdy...

This is a forum post to draw attention to a long standing yaboot bug which has yet to be fixed in Ubuntu.  It specifically manifests when Ubuntu is installed on a 2nd disk on a G5.  The summary: Ubuntu is completely unbootable....a critical blocker which has yet to  be worked on.

Perhaps some pressure from the community will help raise it's priority.  More bug details   in  [Bug 1380](https://bugzilla.ubuntu.com/show_bug.cgi?id=1380).

If noone smarter than me can work on this, can we at the very least have this added to the bounty list?

Edit #1: Reference these corresponding unique topic **Hoary** posts by others in reference to the bug.  This doesn't even take into account the past versions.
[Post #1](http://ubuntuforums.org/showthread.php?t=17419&highlight=g5) 
[Post #2](http://ubuntuforums.org/showthread.php?t=15284&highlight=g5) 
[Post #3](http://ubuntuforums.org/showthread.php?t=13292&highlight=g5) 
[Post #4](http://ubuntuforums.org/showthread.php?t=14886&highlight=g5) 
[Post #5](http://ubuntuforums.org/showthread.php?t=11725&highlight=g5)

Edit #2: I should mention yaboot does work in Gentoo and YDL so it's related explicitly to Ubuntu.  My guess is that it's a debian proc/autoconfig/yabootconfig issue.

---

### Post by petergw on 2005-09-09
**Known Insects:**
[INDENT]I heard that yaboot has a bug that prevents it to boot into the 2nd hardrive. :neutral: 
[/INDENT]


**Install Precaution:**
[INDENT]No Digital Camera[/INDENT]
[INDENT]No External Harddrive[/INDENT]
[INDENT]No Flash Card[/INDENT]
[INDENT]No **(sdb or sdc and anything but sda)** on DiskPartition in the install steps[/INDENT]
[INDENT]Reset PRAM on Powermac G5 after removing anything mention above. (i.e. Cmd+Option+P+R for Reset PRAM)[/INDENT]


**Main Idea:**
[INDENT]Basically when you arrived at **disk partitioner** in the Ubuntu installation software, your internal harddrive should be announced as **and only as (sda)** .



Best of luck for all the Newbie, and of course, the Vets. ;-) 

Peter G. Widjaja
[email]iamanewbietoo@yahoo.com[/email][/INDENT]

---

### Post by TroutMaskReplica on 2005-09-09
i also was unable to install on second hard drive due to the yaboot error - it is not specific to G5s. installation failed on firewire drive using ibook g4

---

### Post by king_arthur on 2005-09-10
Same problem here.
Hoary (and breezy) for the ppc architecture, install just fine on an external hard disk untill the Yaboot has to write the BooLoader. Than it hangs at 50% of OS detection and it's all over.

I wonder why this problem has been neglected for such a long time by the package developers. 
It would add Ubuntu-ppc in incredible amount of freedom as you could use an external HD pretty much the same as we do with the live CD (or OSX).
Actually, the ppc-live CD surely was a much more difficult goal to achieve.

Today the ppc-live CD works flawlessly, I had a go at it recently on my iMac and it really rocks: full hardware recognition, even my iPod shuffle worked in the Rythm BOX! Airport and WEP encryption no problem at all; how comes a simple thing as an installer script for yaboot can't be fixed?

Does anybody know who are the developers of this part of the installer?
May be we should try putting some pressure on the team and priorize fixing this bug as this for sure is a easy thing to fix for somebody with adequate knowledge of OpenFirmware and Yaboot.

/P

**Update**: I have been unfair to the Ubuntu developers... Had a look at Bugzilla  and found [this]("https://bugzilla.ubuntu.com/show_bug.cgi?id=14736"). The Yaboot bug is well known. Only a problem of limited resources. Let's wait and hope for the best...

---

### Post by charlesv on 2005-09-27
I haven't gotten it to work yet (mostly because with my bluetooth keyboard, I keep having to steal my wife's to give it a go), but <a href=http://www.mat.ucsb.edu/~whsmith/cinelerra/debian.html>this</a> seems to be the way to go about getting ubuntu to install. Good luck!

If only it did this automatically...

---

