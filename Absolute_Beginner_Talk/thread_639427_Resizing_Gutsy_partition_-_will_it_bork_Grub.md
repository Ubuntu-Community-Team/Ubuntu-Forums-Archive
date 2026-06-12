---
title: "Resizing Gutsy partition - will it bork Grub?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by raydeen on 2007-12-13
I'm thinking of doing some partition resizing in the future and want to know if I'm going to run into any problems. I know I can shrink my XP partition without problem (XP will just do a disk check the next time I load it up), but will resizing my Gutsy partition mess with the Grub loader? I've seen troubles in the past with Windows when moving the start point of the partition messes up the boot loader. Will the same thing happen with Gutsy?

---

### Post by skymera on 2007-12-13
i cant see why it would mess up.

it's just a resize after all. and you cant move the start point, only the end of the partitiom

EG

1 2 3 4 5 6 
G G G G G 

you can only resize from end

1 2 3 4 5 6 
B B B G G G 

not

1 2 3 4 5 6
B B G G G G

hope my diagram helps.

Btw , G = Gutsy :D B= Blank

---

### Post by raydeen on 2007-12-13
I guess in order to resize the partition, I'd have to move it then. Windows was the first partition, then I installed Gutsy. If I shrink Windows, I'd assume I'd have to move and resize Gutsy to make it larger. Would problems arise then?

---

### Post by innuendosoft on 2007-12-13
What about playing around with your partitions no matter how and then reinstall the boot loader?

---

### Post by kpkeerthi on 2007-12-13
> **raydeen said:**
> I guess in order to resize the partition, I'd have to move it then. Windows was the first partition, then I installed Gutsy. If I shrink Windows, I'd assume I'd have to move and resize Gutsy to make it larger. Would problems arise then?

You should be OK.

---

### Post by weezalxc on 2007-12-13
How would you go about resizing your Gutsy partition? Is there a built in package to do this?

ive thought about doing the same thing in gutsy - I want to make it smaller so I have more room for music, etc.  I store all of my files on my windows partition so I can see them in both Gutsy and Windows.

Thanks!

---

### Post by jken146 on 2007-12-13
> **weezalxc said:**
> How would you go about resizing your Gutsy partition? Is there a built in package to do this?
Use gparted on a live CD.

> I store all of my files on my windows partition so I can see them in both Gutsy and Windows.
I store all my files on my linux /home partition so I can have real permissions in Ubuntu, and use the ext3 driver for Windows (this works best for me partly because I hardly ever boot into Windows). [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by raydeen on 2007-12-13
> **kpkeerthi said:**
> You should be OK.


I'll give it a shot at some point then. Worst comes to worst, I'll just re-install and pull my files off of a backup. That's the one thing I love about Ubuntu. Re-installs are such a breeze. Pain is re-installing software and settings, but I can live with that. Thanks guys.

---

### Post by JillSwift on 2007-12-13
I just finished doing this, plus a few other partition changes including removing old bootable partitions. Grub was fine. :)

---

### Post by ericartman on 2007-12-13
I've used gparted live cd to do this several times and never borked my grub,

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

 
Cart

---

