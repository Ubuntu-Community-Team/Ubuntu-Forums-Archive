---
title: "Dual Boot ( With vista, ew, but need it )"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Cairna on 2007-07-14
Just installed a dual-boot for the second time. I started out with Windows Vista Home Premium, and unfortunately was unaware of the problems people have had with this.

I don't have the install disks, so this problem is rather unfortunate.

Anyway, I resized the partition to 49% with GParted, then installed 

I rebooted, but unfortunately I couldn't see Vista in the Grub menu. So, following a guide, I added this to a file:
```

title Windows Vista

root (hd0,0)

makeactive

chainloader +1

```

After that, it shows up. Unfortunately, when I pick it it says

"Microsoft Corporation" and a loading tab, and it never leaves this screen.

[img]http://www.fewleftstanding.org/forum/gallery/3_14_07_07_10_11_46.png[/img]

Is what shows up in CFDisk. Is it possible I used the wrong command? ( i.e. root (hd0,0) ?

Any help would be appreciated, it'll be hell to deal without them files :/

6.06 LTS Ubuntu

---

### Post by louieb on 2007-07-14
>  
After that, it shows up. Unfortunately, when I pick it it says
"Microsoft Corporation" and a loading tab, and it never leaves this screen.


That means GRUB has done its job and chainloaded the MS Boot loader. If it were XP then you wold run fixboot from the windows XP install CD. Check the dual boot link in sig to see what herman has to say.
 
> Anyway, I re-sized the partition to 49% with GParted, then installed 
 
Kinda late but I've see written to use the native VISTA disk management. something to do with changes to NTFS that GParted cant handle. 
 
I guess at this point its time to search.  see what system rescue CD or trinity rescue kit or super grub has to offer. do check the dual boot site and good luck

---

