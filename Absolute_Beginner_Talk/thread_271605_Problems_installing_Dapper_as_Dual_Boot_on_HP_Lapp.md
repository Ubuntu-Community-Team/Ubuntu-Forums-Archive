---
title: "Problems installing Dapper as Dual Boot on HP Lappy"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by geyerba on 2006-10-04
I've been trying to install Dapper Drake from the Live CD graphical installer on my HP dv1000 laptop and have been caught up on the partioning step.  I've tried several options so far, all of which end up at the same state: a dialog stating "Failed to create enough space for installation".

This laptop has a 100gb fujitsu harddrive with only about 30mb used.  From reading some other posts on other sites, it seems that the partitioner can have problems with certain sizes of partitions, so I've tried both the default and creating custom partitions.  I've also made sure I defragged my hard drive and ran checkdisk on it as well, all to no avail.

Any help would be appreciated as I'd really like to give Ubuntu a try but I still need to keep XP on it (for my wife and kids).

Thanks,
Ben

---

### Post by shanepardue on 2006-10-04
on ubuntu's website you can download the alternate install cd. it's a text-based installer that runs much smoother. i have seen problems like yours with the graphical installer.

can't hurt to try it!

---

### Post by geyerba on 2006-10-05
Thx for the quick reply.  Maybe I'll do that.  However, part of the attraction of the Ubuntu Distro was the graphical installer.  Low barrier to entry.  Surely I'm not the only person with problems with the partioner? 

Ben

---

### Post by geyerba on 2006-10-27
Just to finish up this thread, I did burn an alternate install cd and used the text installer just fine other than a couple of issues.  The first being after rebooting the first time, all I got was a black screen with a couple of white squares.  I used the install cd to repair and afterwards I got the GRUB menu as expected.  Not sure what was up with that.  The other thing is I have a broken package I'm still working to fix.  apt-get and the graphical installers give me errors, so I'm going to try using aptitude next per a suggestion from another thread.  Anyway, thanks for the help.

Ben

---

