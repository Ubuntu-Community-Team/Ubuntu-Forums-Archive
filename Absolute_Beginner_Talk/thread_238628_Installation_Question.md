---
title: "Installation Question"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Seldoms on 2006-08-18
I want to automatically partition, so, is the bar at the bottom of the installation page the space ubuntu will be using?

Say, I want ubuntu to have 8 gigs and the rest to windows. How would I set this up?

---

### Post by Drakkor on 2006-08-18
Here is a nice guide: [http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Seldoms on 2006-08-18
Ive used that guide, but it doesnt answer my question. If I change that bar to 8 gb will my ubuntu partition be 8 gb?

---

### Post by Drakkor on 2006-08-18
Well to be honest,you would have to tell me more about your set-up. Are you using just one hard drive,and the size ? Is Windows already installed ?      I assume you want  to dual-boot. etc.

---

### Post by Seldoms on 2006-08-18
I am running only windows, one harddrive, 32 gb, 21.7 gb free.

Windows already installed. I want to dual boot but I want ubuntu to have 8 gb.

---

### Post by Drakkor on 2006-08-18
I would download the GParted partition editor here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
then following the instructions here:
Play video 3 from here to partition your hard drive
[http://tips.linux.com/article.pl?sid=06/07/20/1654251&tid=129&tid=50&tid=131](http://tips.linux.com/article.pl?sid=06/07/20/1654251&tid=129&tid=50&tid=131)
and make your Windows partition 24Gb leaving 8Gb free and unallocated.
then put your Ubuntu live CD in and install using the "largest contiguous free space available" , which would be your 8Gb partition,it will automatically make the ext3 and swap partition,and install Ubuntu. Make sure you install grub on the master boot record if asked to do so. Good Luck ! :)

---

