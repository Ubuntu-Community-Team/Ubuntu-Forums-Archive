---
title: "Partition Problem"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by NooBeee on 2006-08-08
Ok, so I deceided to install Ubuntu cause it seems like a good way to start learning about Linux. My computer has two hard drives, on 40 gb one and another 120gb. I used QTparted on System Restore CD to shrink the 120 gb NTFS partition down to 80.
Or at least I tried to. The cd crashed on me and I restarted. 

Now Windows is giving me two different hard drive sizes. The disk managenment says that D drive is 80 gb on top, but on the bottom it says it's 120. Also the Ubuntu installer also reports the size as 120 (so i still can't install Ubuntu).

so.....what should I do??

---

### Post by Ludwig7666 on 2006-08-08
I was on windows XP home and is now on Ubuntu. I first had problems to. like I thought I had ubuntu installed the first cuple of times but it wasn't, cause it was the liveCD. What I did to partition was used the ubuntu partitioning program to do it for me. Then after that I could fully install Ubuntu onto my HDD without any problems.

---

### Post by NooBeee on 2006-08-08
Well, the Ubuntu partitioning program doesn't do a good job of resizing NTFS partitions - that's why I used System Rescue CD.

---

### Post by aeiah on 2006-08-08
perhaps a program like partition magic for win xp will help you, if your other partition program isnt reading your partitions properly. its worth a try. or you could try resizing your windows partition to 1mb less, and perhaps it'll correct the errors on the new pass.

---

### Post by NooBeee on 2006-08-08
Yeah, well..unfortunently partition magic and the like are all pretty pricey. I'll probably try the 1mb thing, but I'm staying away from QTparted.

---

### Post by aeiah on 2006-08-08
you could always use partition magic illegally. but i wouldnt condone anything like that, obviously :-\"  there are other alternatives, but if the software you were using lets you try resizing to a slightly different size then that'd be the easiest thing to try first

---

### Post by NooBeee on 2006-08-09
[http://ubuntuforums.org/showthread.php?t=232571&highlight=partition+problem]("http://ubuntuforums.org/showthread.php?t=232571&highlight=partition+problem")

I see there are a lot of other people with problems similiar to me.  
I guess the whole parted (gparted, qtparted, etc) line of software just can't be trusted.

UPDATE: I decided to give the normal Ubuntu partitioner a try (the one with the slider). Lo and behold! I now have a perfectly partitioned hard drive!

---

