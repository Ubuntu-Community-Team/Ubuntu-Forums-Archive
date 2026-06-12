---
title: "Repartitioning Hard Drive"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by germund on 2007-05-04
I just installed Eduntu 7.04, and when I came to the paretitioning question, it gave me a couple of options.  one was to partition at 10.6 gigs, on was to keep the full 20 gigs and one was custom.  since the first option was preselected I assumed that it was going to do something with the other 9.4 gigs so I just clicked OK.  I have since discovered that that 9.4 is lost.  Is there any way I can go back and re-partition to get my full 20 gigs back?  Can I re-install, or something?  I am a complete rookie here.

---

### Post by Churnd on 2007-05-04
If you can unmount the partition with Ubuntu running, you can make changes to it using GParted.  Otherwise you'll have to boot to a live CD with GParted installed to make the changes.  I'm not sure if Feisty has this or not, but there is a Gparted live CD that does only this:  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  Since you don't mind re-installing, go with the partition editor first and see if you can make it work like that.  It would be a good thing to know, especially in using Linux.

What I don't like are partition editors that ask you to resize the partitions based on block sizes.  I never understand how to interpret how big so many blocks is.

---

