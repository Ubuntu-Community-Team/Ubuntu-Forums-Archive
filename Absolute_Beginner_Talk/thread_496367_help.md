---
title: "help"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by kolva on 2007-07-09
I installed ubuntu but i think i messed up with making a partition cause i wanted ubuntu on a 55 gb partition and now my windows got shrunk to 55 and my linux is on an 80sum gb partition... i was wondering if you could tell me how to get rid of ubuntu without destroying my windows partition... i could do this easily from windows...but it wont boot up... it just has a starting up screen and never goes anywhere.....can anyone tell me how....oh..and i need to reset my mbr i know that...i just don't know how....help would be appreciated thanks

(i do intend on reinstalling ubuntu...but after i learn more about how to do things in linux.....i can't figure out how to install any programs or use half of the files if you could send me a link to an easy tutorial on how to do things in linux that would be great too)..thnx a lot :confused:

---

### Post by AlexenderReez on 2007-07-09
below!

---

### Post by AlexenderReez on 2007-07-09
boot from live cd....creat one folder....then mount partition that you have install ubuntu ...... let say folder name 'problem' and partition on 'sd3'....
> sudo mkdir /mnt/problem

> sudo mount /dev/sda3 /mnt/problem

then delete all file in /mnt/problem by

> sudo nautilus


use windows cd to correct mbr.......

---

### Post by kolva on 2007-07-09
i don't have windows cd... my computer didn't come with one when i bought it....and i reformatted a month ago with my friends winxp cd but he lost that cd .....so i don't have acces to a windows cd...

---

### Post by AlexenderReez on 2007-07-09
in that case...it might bring big problem...hm....i don't idea .....but i just want to tell you that windows installer is available everywhere especially in torrent...no,i don't ask you to use illegal thing...just to correct mbr.....grub is not simple problem......unless you able to make backup and reinstall all over again...to do this...see my previous post....figure it out....

---

### Post by kolva on 2007-07-09
i got the windows boot disk from microsofts website...i just dont have six floppy disks

---

