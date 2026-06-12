---
title: "I need help on a complicated reinstall"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Aquilastudio.com on 2007-12-03
As I said in my Apt-Get thread my instalations will run untill 
(reading database...

Reading Database never finishes. In my thread nobody knew what was wrong. I am thinking about reinstalling ubuntu 7.10/ Here are some details.

Originaly I had windows xp dell dimension 4000 something.

I had 0.25 gigs of ram. I added another gig. I added a vido card. A radeon X3000 or something.

I had a 80 gig hard drive that was causing problems from the beginning. 
I bought An external usb hard drive to hold most of my files. My os was howevr on my regular 80gig hard disk.

This summer I decided to doubleboot linux and xp on my computer. That was a big problem to. 

I snet my comoputer to a "proffesional" that had the technology to install ubuntu using a network. The problem seemed to  be that my Samusung Cd drive was not working properly. I had problems partitioning my hard drive.

Finally I had ubuntu 7.4 working well on my computer. I installed compiz-fusion after some reaserch about xgl and ati. When Ubuntu 7.10 came out my computer automaticaly asked me to install it. I pressed Ok. It did the process during the night and by morning it was working. The problem was that all of the things I did to get my ATI graphics card , compiz-fusion and sound to get working in fiesty was gone. I waited about a month before reaserching what to do. I was still installing XGL aln stuff but I always had problems. Half of the screen was usualy covered with noise that looked like "green bricks". I uninstalled XGL. One day I was running the usual

Sudo apt-get install

but it never finished.

(reading database.. was going on forever.

I did not know what to do. I am thinkning of installing UBUNTU on an external hard drive. If so how? Do not forget that my Samusung CD drive will not boot Images. I do however have an external Dvd.Cd usb drive. 

Please help me

---

### Post by stoodleysnow on 2007-12-03
Ee, that sounds like a real pickle.
Suggestion: Upgrade process has been difficult for anyone who used Compiz Fusion in Feisty. Try a fresh reinstall (back up your work first).

---

### Post by Aquilastudio.com on 2007-12-03
The problem is how do I do that? Read my post. (My internal cd drive will not boot images). I would like to install on an external usb drive.

---

### Post by Aquilastudio.com on 2007-12-03
By the way: If it is necessary I might get a new internal dvd drive that would work but what if it is a problem with the bios. When I start a live cd, i hear grinding for a long time but then grub loads.

---

### Post by Aquilastudio.com on 2007-12-03
Edit: I have a phoenix rom bios

---

### Post by LowSky on 2007-12-03
the reason you had a hard time making partitions is because you need to defragment your windows partition before resizing it to fit the linux partitions.

if your hearing grinding  while booting -- thats bad. it means your hard drive may be going.

if your CD drive isn't booting from CDs you need to change the boot order of your drives in your bios...if you want to use an external Drive, make sure you make its availible on your boot list to do so under the BIOS (look for USB device --something[whatever its name is])

---

