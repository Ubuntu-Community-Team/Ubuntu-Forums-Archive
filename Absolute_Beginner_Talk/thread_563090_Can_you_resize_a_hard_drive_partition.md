---
title: "Can you resize a hard drive partition?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-29
I am dual booting ubuntu with windows 2000 because there are some things i need windows for. When i installed ubuntu i used the default partition i was given. Now, in my 60gb hdd, 29.5 gb is for ubuntu and 25 is for windows. I've realized that i need very little hard drive space in windows and would like more to go in the ubuntu partition. Is this possible?

---

### Post by Pumalite on 2007-09-29
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)
Boot from it, right click on the partition and from the menu, choose 'resize'

---

### Post by ryanVickers on 2007-09-29
Yes, with gnome partition editor (gparted) you can resize/move and do lots of things to partitions (depending if your on the program, live CD, and what filesystem it is)

---

### Post by intense.ego on 2007-10-07
I don't understand the part in the documentation about NTFS hard drives. Could someone please explain?
One more thing, in ubuntu when you go to "computer," it says "29.5GB Volume: disk" This is my ubuntu partition right, not my windows one? I want to make sure i don't resize the wrong partition.


EDIT: also, is there anyway of viewing the windows partition in ubuntu without having to reboot into windows?

---

### Post by kevdog on 2007-10-07
If I have bad information but someone please correct me, but I think you can only resize the last partition in the partition list.

Say for example you have 5 partitions - 1,2,3,4,5.  You could delete 5, add the free space to 4, and then recreate 5 if needed if you didnt allocate all the space for 4.  If you wanted to add space to 3 for example, you would have to delete 5 and 4 -- imaging adding space to 1 -- you would have to delete partitions 2-5 -- oftentimes this is not want you want to do.  So in many cases you can not add free space to partitions unless you end up deleting partitions that were created after it.  Wish someone would have told me this when I created a boot partition on hda1 and the main partiion on hda2

---

### Post by Pumalite on 2007-10-07
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

