---
title: "Am I stuck with the &quot;official&quot; ATI drivers?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-11
After initial installation, I was using vesa drivers.  I used the resticted drivers manager to load the official Ati drivers that everyone says suck because I figure some acceleration is better than no acceleration.  I come to find out I can't use desktop effects from the system -> preferences menu with these drivers because, after searching the forums for a solution, ati simply doesn't offer linux support worth a dang.  So I went on a quest to find the open source drivers which I thought were going to offer better results.  I found [this]("https://help.ubuntu.com/community/RadeonDriver") and followed the instructions up until restarting xserver.  I restarted xserver, tested the driver following the instructions, and it said direct rendering "yes" so I thought it had worked.  About 2 seconds later, it crashes.  I reboot and am worried because this is the same type of freezing I've been struggling with for the last 2 days.  It crashes again at the login prompt.  I boot up a rescue disk and restore xorg.conf, reboot and am now back on the "official" ati drivers.

Am I stuck with them?  Is there something I might have done wrong in xorg.conf to cause the crash, or is this simply a problem that is unsolvable as of now?

I'm running a Radeon 9500 Pro AGP video card.

---

### Post by matthew.lns1 on 2007-08-11
If you want 3-D accsereation and the other driver made you crash I think your stuck. But maybe someone else will have a solution.

---

