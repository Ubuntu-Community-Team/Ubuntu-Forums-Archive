---
title: "where is &quot;c&quot; drive"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by mszl_1 on 2005-12-20
i tried to save some work i did on fedora core 4. all be it im new to linux as i have been playing with it for about 1 week now and so far its good. where is the "c" drive in fedora/ ubuntu as the names of files etc is still a bit confusing. ill learn sometime but for now i need some guidance. thanks

---

### Post by lreyes6 on 2005-12-20
with de "c drive" you mean the root folder? 
the root folder is " / " but 

when you save something from almost any program it goes to the "/home/user" folder in my case is "/home/lreyes6"

---

### Post by Enter on 2005-12-20
if in anyway you mean you want to access the other partitions try reading this :D
[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

---

### Post by schdefan on 2005-12-20
In Linux you don't use letters for drives. The naming is a little bit different.
Let me explain on a short example how linux is organized with harddiscs. I assume we have 2 IDE hardrive on first IDE Controller. One harddrive with 3 partitions and a second harddrive with only one partitions
The names for the first harddisc would be:
[LIST]
[*]first partition: /dev/hda1
[*]second partition:/dev/hda2
[*]third partition:/dev/hda3
[/LIST]

The name for the second harddisc would be:
[LIST]
[*]first partition: /dev/hdb1
[/LIST]


And once more we have 2 hardrives on the second IDE Controller with one partitions the names would be:
[LIST]
[*]first partition: /dev/hdc1
[*]second partition:/dev/hdb1
[/LIST]
To sum up. IDE harddrives are characterized with hda, hdb, hdc, ... depending on which controller port they are connected. 
Partitions are identified with numbers.
If you take a look at the file /etc/fstab open a terminal and type
> $cat /etc/fstab
you will see your filesystem table. All the devices named as /dev/hdaX are mounted to some directory. Normally /dev/hda1 is mounted to /mnt/hda1

If you install for example Windows on /dev/hda3 then you can find your C drive in /mnt/hda3.


If you are using SATA drive then you have sd instead of hd.

schdefan

---

### Post by mszl_1 on 2005-12-20
thanx for the replies. i see that i have loads to learn, thing is windows disables people and they dont even realse it!
does this however mean that when i save work it will automatically go to "/home/mark" as it would be in my case?
i suppose ill just have to try it and see what happens eh?;)

---

### Post by bscbrit on 2005-12-20
Its not relevant to this thread - but 'Windows disables people' struck a chord!

---

### Post by mszl_1 on 2005-12-22
bscbrit i agree with you as far as a lack of knowledge is concerned! what i meant was in windows you can only do things the way microsoft dictates, but with linux there seems to be a greater range of things that can be done. i have been using linux for about 1 week now and with my limited knowledge i have achieves far more in linux that i did when i started using windows. i crached my windows umteen times in a short period of time through no or lack of knowledge mind but in linux this  is limited since you need to be root to do so!
linux gives room for development and customising the pc to individual needs where windows gives you a package and you need to accept it as it is.;)

---

