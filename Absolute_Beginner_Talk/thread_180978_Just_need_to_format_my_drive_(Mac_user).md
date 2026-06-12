---
title: "Just need to format my drive (Mac user)"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by rui_mac on 2006-05-23
I have a faulty hard drive that refuses to format  with the Disk Utility, from OSX.
I was told to try to format it with ubuntu, as a by-product of the instalation process.
I have both CDs, the live version and the install version.
What should I use to format my drive and what exactly should I do?
I'm completely  "virgin" in Linux/ so, bear with me, ok? ;)
Could someone give me step-by-step instructions on what should I do?
Thank you very much in advance.

Rui Batista

---

### Post by Gimbo on 2006-05-23
You can use either

With the Live CD, just put it in your computer and restart. Once in Ubuntu, go to Applications > System Tools > GParted. Use GParted to delete all the partitions (there might only be one) on your hard drive.

With the Install CD, put it in your computer and restart, just as you would with the Live CD. Go through choosing all the default options (it doesn't matter seeing as you're not trying to install Ubuntu) and when you get to the partitioning bit, you can delete all your partitions.

I recommend using the Live CD because GParted is probably more user-friendly than the Ubuntu installer process.

---

