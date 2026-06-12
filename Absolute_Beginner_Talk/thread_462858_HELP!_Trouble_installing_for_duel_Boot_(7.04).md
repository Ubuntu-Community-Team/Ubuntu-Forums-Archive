---
title: "HELP! Trouble installing for duel Boot (7.04)"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-06-03
My friend turned me on to the idea of Linux, so I burned Ubuntu onto CD without any problems.
I want to have the option of duel booting. I have read various forums on this matter, and saw a video that talked about duel boot install with 6.10. I have 6.06.1 and 7.04, and I like 7.04 better.

Thus far, all the forums I have read have been for everything BUT 7.04.

I am pretty computer savvy with hardware, but the software is my downfall.

Is their anyone here who could help me navigate Ubuntu, and aide me on my quest of having a duel boot computer for the specific install of 7.04?:popcorn: I will share my popcorn!

---

### Post by alienexplorers on 2007-06-03
Its very easy.  If you have windows on already you just need to resize partitions to make room for 7.04.  Then load 7.04 which will setup grub and you should have dual boot.

---

### Post by Tux Aubrey on 2007-06-03
It really is quite straight forward.  

Check out [[COLOR="Navy"]_**this site**_[/COLOR]]("http://psychocats.net/ubuntu/index") for some guidance on selecting a partitioning design that will do what you want.

The CD will also guide you through when you select "install".

(BTW - Most of the discussion about installing will be relevant for 6.06, 6.10 and 7.04 - Installation from a Live CD is almost exactly the same).

---

### Post by Akuma Shiro on 2007-06-03
Do I use "guided - use entire disk"
Or "Manual" ?
For the partition section?

---

### Post by Akuma Shiro on 2007-06-03
> **alienexplorers said:**
> Its very easy.  If you have windows on already you just need to resize partitions to make room for 7.04.  Then load 7.04 which will setup grub and you should have dual boot.

I went to "Guided" and to "Manual" for the partition section, and thus far, all I can do is install completely over everything I have, or edit existing partitions. Nothing about resizing.

When I was playing around with 6.06, their was a thing where I could resize my windows partition, but I would rather have 7.04.:(

---

### Post by alienexplorers on 2007-06-03
The easiest way to setup dual boot would be to save your important data.  Then format your drive.  Make a partition for Windoze, one for linux root, one for linux home, and a small 1gb swap file.  Then load windows onto the windoze partition.  Then load ubuntu 7.04 into the 2 partitions you made.  After it is done you should be dual booting.  This is the way I did it and it worked like a charm.

---

### Post by Akuma Shiro on 2007-06-05
I read an article for dual booting, and the guy (or girl) installed a second hard drive and installed Linux onto that. So, thats what I ended up doing. Works great! I'm going to keep windows for a few programs, until I can get the virtual windows working.

Thanks for all your help and info!

:KSLoving Linux!:KS

---

