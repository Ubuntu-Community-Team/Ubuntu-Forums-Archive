---
title: "Grub Error 17"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2006-09-06
I have not changed my partitions or anything of that nature, all of a sudden after I rebooted windows, I get a Grub error 17.

I have no Idea what is wrong, besides the fact that I dual boot windows and ubuntu.

---

### Post by cnc333 on 2006-09-06
no solution here, but rather the same problem, kinda. I had everything working good and dual booting when my mobo went out and i decided to upgrade hardware and reinstall windows. then when i booted, grub was gone... so i followed a HOW TO guideo on reinstalling grub. it works when booting windows but not when i try to boot into one of my linux partitons. I get an error 17 message. it says unable to mount the selected partition, or something to that nature. What i think is my problem, is for some reason my new mobo labels the HDD diferent than my old one. im not real sure though. so, i need some way to edit my menu.lst file or something even though i cant boot into ubuntu. any help is greatly appreciated and thanks in advance

---

### Post by unconquerable on 2006-09-06
Still cannot figure out the problem.  I did not replace any hardware what so ever.  Nothing that I am aware of has changed on my system.  It has worked fine for over a month.

I am kind of desprate as a lot of my school work is on here. I can get it off using the live cd... I think, but I would like to correct this problem instead of taking the long road of reinstalling everything.

running off the live cd atm

---

### Post by jISh on 2006-09-06
edit: double post.

---

### Post by jISh on 2006-09-06
Boot into LiveCD go to terminal.
Use the following commands:
```

chroot /mnt/sysimage # i think and hope that's the one for ubuntu..lol
grub-install /dev/hda

```

If it still doesn't work, check the /boot/grub/menu.lst
If Windows is in the first partition of your hard drive it should look something like this in your WinXp section.
If it's in another partition, remember grub counts from 0, so if it's in partition 2 of your first hard drive, it's (hd0,1).

title Windows XP
        rootnoverify (hd0,0)
        chainloader +1

---

### Post by unconquerable on 2006-09-07
I tried the stuff above, but it seems to not be able to find the partition.  When I look at "Computer" I can see all the partitions BUT the Ubuntu one, and if I try to load ANY of them they wont mount.

---

### Post by unconquerable on 2006-09-07
Does someone at least know how I can get access to any/all the partitions so I can reformat the sucker?

---

