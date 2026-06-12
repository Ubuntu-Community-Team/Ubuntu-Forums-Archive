---
title: "new installation... cant boot into it for the 1st time"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by banda on 2007-06-10
i just finished installing ubuntu 7.07 on my pc
but after installing and restarting... i was given 3 options for ubuntu and one vista.. 
the problem is if i choose any ubuntu option it gives me error 17: cannot mount selected partition
and that ubuntu detected vista is also wired as i uninstalled it long ago ( it does not show xp which i do have installed).. 

i m on the live cd now.. can i correct it from here??:(

---

### Post by FleetAdmiral74 on 2007-06-10
Could you go into gParted and take a screenshot of the partitions it shows? If you have more then one HD be sure to get em all, that should help.

---

### Post by banda on 2007-06-10
[IMG]http://img453.imageshack.us/img453/8105/screenshotdevhdbgpartedjs1.png[/IMG]



[IMG]http://img392.imageshack.us/img392/6941/screenshotdevhdagpartedsu5.png[/IMG]



this one is external usb
[IMG]http://img365.imageshack.us/img365/8540/screenshotdevsdagpartedhq3.png[/IMG]

---

### Post by FleetAdmiral74 on 2007-06-10
Is your ubuntu install on the fat32 or the ext2?

edit: two more? holy crap, forum admin's I'll need backup!

---

### Post by banda on 2007-06-10
its on ext2


one of 'em is usb.. 2 on the main pc(i think u read the mssg after i posted screens for all 3... i had written it after putting the screenie for just the 1st 1)

---

### Post by FleetAdmiral74 on 2007-06-10
Well good sir, I think I have found your problem. You cannot boot from an extended partition, only a primary.

---

### Post by banda on 2007-06-10
how do i fix it??
and r u sure ??. cuz i had another linux running from it before

---

### Post by FleetAdmiral74 on 2007-06-10
Well I am pretty sure...

And about fixing it, maybe look for a way to convert extended to a primary? Cause it looks like you only have 3 primary partitions, so you could fit one more. Why, if I may ask, did you choose to use an extended and not a primary like your other partitions?

---

### Post by banda on 2007-06-10
i wanted to have seprate root and /user partitions.. 
i think i will take the simpler way and just delete the extended partition and do a reinstall..
i know i can have only 4 partitions on a drive but is swap counted??..
could u sugest a way??
ooh and thanks for your help :)

---

