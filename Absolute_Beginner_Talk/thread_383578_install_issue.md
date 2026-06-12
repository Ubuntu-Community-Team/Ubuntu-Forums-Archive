---
title: "install issue"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by 12tipp12 on 2007-03-13
Hi folks, im new to ubuntu and have probs/issues installing,  my pc is set up like this, 1st installed hd is 80g partioned 40/40,  1st(c) has xp pro, 2nd(e) has xp home, also i have an external 20g disk installed(i) which contains 2 images of 1st disk( 1 using ghost & 1 using true image) which has roughly 1g of space left, also i have another external 80g disk installed and partitioned at 55g(j) & 25g(k),  i want to install ubuntu into partition k,   Ive tried installing but when i get as far as page 5 of the 6 step installation it gets a bit scary and im not sure what to do next, i think it wants to install grub on c, whereas i was hoping to have everything installed on k, keeping it all in the same partition or if i have to can i use k instead of c/e, Sorry for the confusing post and im a real newbie so excuse my lack of knowledge also. any help/advice will be much appreciated and thanks in advance.

Bill.

---

### Post by penp on 2007-03-13
> **12tipp12 said:**
> Hi folks, im new to ubuntu and have probs/issues installing,  my pc is set up like this, 1st installed hd is 80g partioned 40/40,  1st(c) has xp pro, 2nd(e) has xp home, also i have an external 20g disk installed(i) which contains 2 images of 1st disk( 1 using ghost & 1 using true image) which has roughly 1g of space left, also i have another external 80g disk installed and partitioned at 55g(k) & 25g(k),  i want to install ubuntu into partition k,   Ive tried installing but when i get as far as page 5 of the 6 step installation it gets a bit scary and im not sure what to do next, i think it wants to install grub on c, whereas i was hoping to have everything installed on k, keeping it all in the same partition or if i have to can i use k instead of c/e, Sorry for the confusing post and im a real newbie so excuse my lack of knowledge also. any help/advice will be much appreciated and thanks in advance.

Bill.

grub is a boot loader, it needs to be written to the MBR on your primary drive or you wont be able to boot to linux unless you can set it up somehow to boot from a cd or floppy disk (which i assume would be possible by installing grub to said disk)

---

### Post by 12tipp12 on 2007-03-13
Thanks penp, that makes sense, but im a little concerned as to whether it will mess up the os,s on that disk and if it might cause a conflict with either of the 2 os,s , and what effect it will have if i dont have the external disk containing ubuntu switched on when i boot the pc, again any help/advice is appreciated and thanks again penp.

Bill.

---

### Post by dstew on 2007-03-13
One issue that might be causing some confusion is the difference between how windows names disks and partitions, and how linux names them. In windows, the letters you refer to, c to k, need to be translated into the native linux disk and partition names. Then we will undertstand better where your linux installation should go.

To make a list of your current partitions that will be understood by linux people, you can use the partition editor on the install disk, and post to the forum what partitions are listed. Another way is to open a terminal window while running the LiveCD, and enter on the command line:

fdisk -l

This will list the partitions as seen by Ubuntu. Linux people often use the command line to help set up systems, because there are so many varieties of linux that differ with respect to the graphical user interface. Ubuntu itself has many varieties. The command line is a constant anchor behind the glitz and glamour of the GUIs.

---

### Post by 12tipp12 on 2007-03-13
Thanks dstew,  i will do as you suggest and then you will have a better idea as to where/what im trying to do.

Bill.

---

