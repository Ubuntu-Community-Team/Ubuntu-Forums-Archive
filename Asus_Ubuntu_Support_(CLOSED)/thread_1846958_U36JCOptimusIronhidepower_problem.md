---
title: "U36JC/Optimus/Ironhide/power problem"
date: 2011-09-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jarl-haggerty on 2011-09-19
When I first had some problems with my ASUS U36JC laptop I found this thread, I think the crux of my problem now is turning off the nvidia card,

[http://ubuntuforums.org/showthread.php?t=1705406](http://ubuntuforums.org/showthread.php?t=1705406)

I followed all the instructions in there and when I looked at the power consumption after turning off the nvidia card I had just a little bit more than he did, a little above 10000mW.  Then I read the rest of the thread and did some searching and learned about ironhide, which would let me toggle and use the nvidia card.

I installed ironhide but now my power consumption seems to have sky rocketed.

jarl@jarl-U36JC:~$ sudo /usr/local/bin/ironhide-disablecard
DOFF Disabling nVidia card succeeded.
jarl@jarl-U36JC:~$ grep rate /proc/acpi/battery/BAT0/state
present rate:            47432 mW

---

### Post by jarl-haggerty on 2011-09-20
I realized that between installing ironhide and when I posted this thread that I had never actually powered down the laptop.  I rebooted and my power consumption is much more reasonable.

[http://www.youtube.com/watch?v=p85xwZ_OLX0](http://www.youtube.com/watch?v=p85xwZ_OLX0)

---

