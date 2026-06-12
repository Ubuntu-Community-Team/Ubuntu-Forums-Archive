---
title: "Help with Dual-Booting."
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by TheCyrus on 2005-10-15
So I read the wiki, and I've asked for help in the chatroom, but i still can't get it to work.

I have a Breezy Install CD and I want to install it to a partition that i have made so i don't harm my windows installation whatsoever.

I select manually edit partition tables and i end up setting it like this.

Linux D Drive #1, Primary, Fat32, Mount Point: /, Default Mount Options, Boot Flag Off, Size 4.0 GB

Swap Drive # 3, Swap Area, Mount Point: N/A, Mount Options N/A, Boot Flagg Off, Size 559.3 MB

Windows C Drive # 2, NTFS, Mount Point, /media/hda2, Mount Options N/A, Boot Flag Off, Size 75.5 GB

So what am I doing wrong, everytime i try to install, i get a debootstrap error (return value 1) check /target/var/log/bootstrap.log

Am i even on the right track?

Thanks.

---

### Post by aysiu on 2005-10-15
This tutorial walks you through it step by step (with pictures):

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Griff on 2005-10-16
That link was a HUGE help.  Spent a good part of the day browsing the forums, which was very informative, but having a step-by-step guide was nice for my newbie self.  Made for a lot less stressful day just knowing what was going to happen next.  On a side note, my first ever Linux OS install went beautifully.  Ubuntu runs smoothly and all hardware was immediately recognized.:p

---

