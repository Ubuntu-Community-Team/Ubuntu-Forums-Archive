---
title: "Mounting root file system problem, no tty, job control turned off"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-26
I am very new to linux and this is the first distro i tried. I installed everything 1gb swap file, 8gb for linux, adn then the rest for windows and my documents on an 80gb sata HD. I installed linux's boot folder on the sda4 partition. I've read at this link how to fix it but it does not work. 

[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)

At step 9, shown in the picture [http://www.lost-doggies.com/temp_graphics/Screenshot.png](http://www.lost-doggies.com/temp_graphics/Screenshot.png)
mine shows 
Device: /dev/sda4
Filesystem: unknown
Status: inaccessible

I find this odd because i have formatted this to ext3 as i installed linux using the livecd. I really want to get this to work to begin my exploration of linux and possibly the transition from windows to ubuntu. Please any help would be appreciated. 

So my problem i beleive is that it doesn't see my sda4 partition. When i tried to mount it said no such file.

---

### Post by noodles12 on 2006-07-26
Did anyone else solve/have this problem?:-(

---

### Post by adam0509 on 2007-01-27
Not sure if it will works for your problem but...

F6 + irqpoll

Thanks to answer if it works for you

---

