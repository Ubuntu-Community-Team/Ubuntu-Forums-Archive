---
title: "[SOLVED] MBP and Dual Boot MAC OS X &amp;amp; Ubuntu Studio"
date: 2008-07-03
forum: Apple Hardware Users
---

### Post by umbrAtrorum on 2008-07-03
all right, i'm (almost) sure this is a stupid question: i got my new macbook pro (2.5 Ghz Intel Core 2 Duo, mac os x leopard) and am, as musician, pretty eager to have mac os x AND ubuntu studio running on it. i guessed for now that if possible i will avoid refit. i installed boot camp, resized the mac partition to create space for my linux. rebooted, entered ubuntu studio setup, created 3 linux partitions (/,/home and swap) in the free space, installed ubuntu, rebooted --> no bootable device found. then, i read in [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro), that the way mac partitions his drives needs those weird free spaces between existing partitions. so i re-installed my mac os x, followed the exact same procedure as above, but this time i created my linux partitions with the exact same free disk space before them as the mac partitioner had left it and reinstalled - same thing. what am i doing wrong? i noticed that the last thing that the ubuntu studio setup does is to install grub. does this mess up my mbr? is there a way to keep the ubuntu studio installer from installing grub? or is the problem elsewhere? i'm not sure if using refit will cover for this problem, because even with refit the question about the free space before the linux partition and the issue about grub remain. i'd be grateful for help on this. thanks in advance!

jaspeR

---

### Post by pxwpxw on 2008-07-03
Have a look at  this 
 [all variants] Intel Macs with Hardy 'no bootable devices'  cyberdork33
[http://ubuntuforums.org/showpost.php?p=4795505&postcount=1](http://ubuntuforums.org/showpost.php?p=4795505&postcount=1)

and the weird free spaces are not required.

---

### Post by umbrAtrorum on 2008-07-03
i don't know how to thank you =D>

it worked. i installed refit, reduced the size of the mac partition, installed ubuntu studio in the empty space. rebooting, i allowed the partitioning tool from refit to fix the mbr, then, with a live cd i followed the instructions from [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11) and that did the trick!

the only thing is now that in the refit menu, two tux symbols appear :confused: ... both actually boot ubuntu studio. if anybody knows what to do about that, it'd be interesting to know, but even with one symbol too many in the refit menu everything works. that's what i care about. thanks again!

jaspeR



ps: how can i mark this thread as solved?

pps: stupid me. got it :)

---

### Post by cyberdork33 on 2008-07-03
you have two tux icons because you have likely got grub installed in two different places now. One in the MBR, the other on your Ubuntu partition. The latter is really the better place. 

You can try this to clear out the one from the MBR, but if you can live with two icons, I would just leave it alone.
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

