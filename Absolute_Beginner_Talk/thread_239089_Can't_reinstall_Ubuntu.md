---
title: "Can't reinstall Ubuntu"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by reldruH on 2006-08-18
I'm going crazy trying to figure out why I can't *re*install Ubuntu. It's already on my computer, I just want to reinstall it to get rid of lots of programs and files left over from KDE. I ordered CD's from ShipIt, got them, tried to use them and at the partitioning step in the install process it always hangs, whether I resize the main partition or try to edit manually, it always hangs. I figured there might be something wrong with the CD so I downloaded the latest iso, burned it and ran into the exact same problem. The installer just won't get past step 5. Any ideas?

---

### Post by Drakkor on 2006-08-18
I would download the GParted partition editor here,and just delete the whole partition or drive for that matter and start over.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by ComplexNumber on 2006-08-18
> **reldruH said:**
> I'm going crazy trying to figure out why I can't *re*install Ubuntu. It's already on my computer, I just want to reinstall it to get rid of lots of programs and files left over from KDE. I ordered CD's from ShipIt, got them, tried to use them and at the partitioning step in the install process it always hangs, whether I resize the main partition or try to edit manually, it always hangs. I figured there might be something wrong with the CD so I downloaded the latest iso, burned it and ran into the exact same problem. The installer just won't get past step 5. Any ideas?
thats a common bug - when i first tried to install dapper, it crashed about 7 or 8 times consecutively whenever i pressed the back button. the trick is to go through the custom partitioning without pressing the Back button to change something. i ended up losing all the data on my home partition because of it. if you're going to resize, USE WITH CAUTION and make sure that you get everything perfect first time.

---

### Post by reldruH on 2006-08-18
> **ComplexNumber said:**
> thats a common bug - when i first tried to install dapper, it crashed about 7 or 8 times consecutively whenever i pressed the back button. the trick is to go through the custom partitioning without pressing the Back button to change something. i ended up losing all the data on my home partition because of it. if you're going to resize, USE WITH CAUTION and make sure that you get everything perfect first time.
Thanks for the advice but that wasn't my issue. I wasn't pressing back, it was just hanging no matter what options I selected. Luckily somebody earlier in this thread showed me GPart and that solved all my problems. Thank you, though :)

---

### Post by reldruH on 2006-08-18
> **Drakkor said:**
> I would download the GParted partition editor here,and just delete the whole partition or drive for that matter and start over.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
*Thank you!* That was perfect, exactly what I needed. I downloaded it, burned the CD, used it and deleted all my Linux partitions and the installer went through without a hiccup. I will always keep a GParted CD ready now. It's incredibly useful, as was your reply. Thank you!

---

