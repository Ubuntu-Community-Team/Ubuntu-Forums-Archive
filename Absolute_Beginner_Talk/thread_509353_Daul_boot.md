---
title: "Daul boot"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Dark_X on 2007-07-25
I had Vista installed on one of my partitions and now that I have installed Ubuntu on another partition I can't boot into Vista.  How do I setup a dual boot system in Ubuntu?

---

### Post by sci-fi guy on 2007-07-25
Did you make the partition during the Ubuntu install process or before?

---

### Post by Dark_X on 2007-07-25
I made a second partition in vista but reformatted it in ubuntu.  Does anyone know how to add vista to the grub boot thing?#-o

---

### Post by MQMike on 2007-07-25
You just have to edit the boot menu in Ubuntu to include a valid boot entry for your Vista.

The following boot entry for Vista goes into your boot menu, which is the file /boot/grub/menu.lst in your Ubuntu:

title  Vista
rootnoverify (hd0,0)
chainloader +1
boot

(You edit that file using root privileges and don’t for get to save your changes.)

Did you have Vista on the first partition of your hard drive?  If so, that’s (hd0, 0); if not, that might be an issue and you have to make adjustments.

First, check your menu.lst to see if Vista in included (as above).
Then write back and tell us exactly what is on your hard drive (and what partitions).
(If you get a Terminal in Ubuntu, the command sudo fdisk -lu  will give information about your hard drives.  That –lu, “l” as in “list,” “u” as in “units.’)

This How-To tells you how to edit menu.lst (see the second post):

[http://kubuntuforums.net/forums/index.php?topic=3081671.msg81008#new](http://kubuntuforums.net/forums/index.php?topic=3081671.msg81008#new)

---

### Post by Dark_X on 2007-07-25
Thank, thats was exactly what I was looking for!:)

Edit: It didn't work. Should I change it to (hd0, 1) or (hd0, 2)?

Edit2: Changing it to (hd0, 1). It works!

---

### Post by MQMike on 2007-07-25
Good!

Interesting.  So Vista was on your (first) hard drive, the second partition (hd0, 1)?

Now when you turn on your PC, the boot menu shows both Vista and Ubuntu and you are able to choose either and boot into your choice, right?

---

### Post by Pebbie on 2007-07-25
im not sure how to... but i have 3 OS running now. i have 2 HDD, 150gb for my XP, then the 250gb HDD i partition to 100, 100, 50. then i install vista on the 100gb and ubuntu on the other 100. no prob while install or after install. i can run my vista, XP and ubuntu. and i dun pay for my windows

---

