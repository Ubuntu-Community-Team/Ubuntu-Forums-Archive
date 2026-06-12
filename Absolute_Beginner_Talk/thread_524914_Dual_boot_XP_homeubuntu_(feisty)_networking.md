---
title: "Dual boot XP home/ubuntu (feisty) networking"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by johnnyblack87 on 2007-08-13
Just a question, if i network two hard drives through XP will they still show up if I boot to Feisty instead of XP?

---

### Post by ugm6hr on 2007-08-13
> **johnnyblack87 said:**
> Just a question, if i network two hard drives through XP will they still show up if I boot to Feisty instead of XP?

I am fairly certain the answer is no.

You would have to mount the shared drive in Ubuntu separately.

---

### Post by johnnyblack87 on 2007-08-13
ok well I'm having some problems with that. The drives have been mounted in ubuntu and shared over the network. The feisty box can see the network and recognizes that it is on the network but can't see the xp home laptop thats on there as well. the laptop is on the network but cannot see the feisty box. any suggestions?

---

### Post by crav on 2007-08-13
I can't be absolutely certain this will have your answer, but this had everything I needed when I networked my computers. This is just about everything you could ever need to know about samba.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+map+network+drive](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+map+network+drive)

---

### Post by johnnyblack87 on 2007-08-14
i walked through the suggested HOWTO and it worked. Momentarily. Both computers are hooked up through wireless internet and i'm a bit unsure on how to get a static ip for this machine. Also, it didn't say how to add two drives. once again your help is greatly appreciated.

---

### Post by ugm6hr on 2007-08-14
Network Manager (NM) doesn't support static IP (which is presumably what you use to connect wifi).

Options:
1. Use Wicd instead of NM - and give each computer a static IP
2. Stick with DHCP, and accept that you will have to mount each networked machine following each reboot.  You could try using pyNeighborhood - which is very straightforward to use (although I believe it should be possible from Network Places in Ubuntu)

Helpfully - these 2 things are links in my signature below.

This is a pretty good link (video tutorial): [http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

