---
title: "How do i delete partitions from my HD?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by The AlGorenator on 2007-03-18
Anyone know how i can delete partitions from a drive?

---

### Post by zekopeko on 2007-03-18
try gparted from the repos.

o, and you need to unmount them first i think.

in terminal:

sudo umount /dev/<hard drive tag here ie. hda1, hdb2 etc>

---

### Post by The AlGorenator on 2007-03-18
sorry? that made v/ little sense to me.

if it's simpler, how can i do it from windows?

---

### Post by AtrejuT on 2007-03-18
open up synaptic, look for a package called gparted and install that.
run gparted, select the partiton you want to delete. right click, select unmount. right click it again, select delete. select apply.

atreju

---

### Post by The AlGorenator on 2007-03-18
sweet, thankyou!

---

### Post by laidback on 2007-03-18
Gparted is the standard Ubuntu Partitions editor. It's available via Systems>Administration>Gnome Partition Editor if you're using Gnome that is. You'll be asked for your password as usual.
Remember that you cannot edit a partition that is mounted, but, the live CD has it too. Or failing that download a live version of Gparted and burn your own bootable CD. I prefer the later as the version of Gparted is up to date, 0.3.3, Ubuntu's version is 0.1 and for one thing doesn't like USB flash memory sticks. Otherwise I believe v0.1 is OK.

Live CD here:-

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

documentation here:-

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by yabbadabbadont on 2007-03-18
I was going to suggest a very, very small hammer and chisel... but your replies were better.  :D

---

