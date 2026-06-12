---
title: "grub error 15"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Roofie on 2007-12-07
When i reboot my system this morning it would not reboot
Grub error 15
Well i have read many posts on grub errors.
I can only boot now using super grub disk.
I used the option to repair and still get error 15
another post i followed a link 
```
http://ubuntuforums.org/showthread.php?t=224351
```
followed the steps every thing went well 
Still when i reboot error 15
I never edited anything i only rebooted

---

### Post by wolfen69 on 2007-12-07
see this page [http://www.statusq.org/archives/2007/01/07/1267/](http://www.statusq.org/archives/2007/01/07/1267/)

---

### Post by Roofie on 2007-12-08
Thank you for the link wolfen69
So after reading the link there i started to look around in the bios.
Every thing was fine ?
So i shut down my system unhooked my 500gig maxtor.
Started and it started fine.
So i shut down my system and hooked the 500gig back up!
Still booted fine, But now the 500gig does not show at all.
So i run gparted, gparted show my drive as unallocated ?
What would cause this problem ? The hard drive was bought on October 10,2007 
Is only 2 months old.
Is there anything i can do to get my movie files back or just take it as a loss.

---

### Post by bumanie on 2007-12-08
You could trying to recover your partition and data with test disk (open source product). It apparently works very well

---

### Post by Roofie on 2007-12-08
Ok i checked out that program and it came out with a number like 28hrs to scan.
So i tried something different !
Since the origanal problem error 15 seem to come from the 500 gig being attached,
I unhooked my 10gig that the main operating system is on.
Threw in the gutsy cd, Let it boot.
Well now i can see both partitions on the 500 gig !
I can go in all files are fine ?
Why will these hard drives not play good together ?
For 2 months there was no trouble till yesterday when i reboot.
Im just totally lost on what to do other then re install to the 500 gig

---

### Post by bumanie on 2007-12-08
About 2 months ago, I installed a seagate hdd as a slave and since then I have had nothing but grief from grub etc. Don't know whether it is the drives being incompatible or if it's me hooking things up wrong (I think they're cabled and jumpered together correctly). These things can be frustrating, but sorry I don't know the answer to your question.

---

### Post by squiggs on 2007-12-08
Roofie -

If I was you I would do the following.


Allow Ubuntu to boot from the Hard disk, (10GB). From there try and diagnose the problem with the bigger disk. You may not be able to see it because it isn't mounted.

Try fdisk - l 

When your inside Linux, and post the results. 

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html) - also post what part of Grub the problem is with. Stage X for example. Im only a newb myself, so maybe some of the more knowledgeable guys will help you out.

---

### Post by Roofie on 2007-12-08
Thanx guys for the ideas.
I did make a mistake bumanie the 500 gig is seagate.
when the 2 drives are both hooked up is when i have troubles error 15 and 1 time error 17
I have been using linux only 1 year now and very slow learner.
It took me 6 months to even touch the terminal.
And now have stopped using windows completly
I think im gonna choke it up and just install to the 500 gig and toss the 10 gig aside.
Thank you all for your help !

---

