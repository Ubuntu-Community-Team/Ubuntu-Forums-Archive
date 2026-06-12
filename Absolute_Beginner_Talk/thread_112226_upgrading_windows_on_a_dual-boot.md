---
title: "upgrading windows on a dual-boot"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-01-03
i have ubuntu and windows 2000 dual booting on my computer and i was wondering if upgrading windows 2000 to xp would have an effect on ubuntu, particularly GRUB

---

### Post by darth_vector on 2006-01-03
it will remove GRUB from the master boot record. go ahead and install it, then restore GRUB with this:

[http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by notquitehere188 on 2006-01-04
thanks, but how do i get into ubuntu to run that command

---

### Post by proventech on 2006-01-04
is ubuntu and windows on separate hard drives or just different partitions of the same drive?

---

### Post by darth_vector on 2006-01-04
[QUOTE=notquitehere188]thanks, but how do i get into ubuntu to run that command[/QUOTE]

did you read the "How to use Ubuntu Installation CD, to gain root user access" bit (step 2 of the how to)? this explains it for you.

---

### Post by notquitehere188 on 2006-01-04
Thanks :)

---

