---
title: "How to partition"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Lardadart on 2007-04-03
Can you make 2 partitions of an existing partition and if so, how. I know this is a total newbie question.

---

### Post by theratwonder on 2007-04-03
I Actually know nothing about Ubuntu per se being a total newbie myself, but when I did my partitioning I used "Live GParted" - you just create a boot CD from an ISO you download, and run it, and you can split partitions, resize them, create new ones... Worked a treat for me.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Robin.

---

### Post by Lardadart on 2007-04-03
Thanks I'll check it out.

---

### Post by nsleiman on 2007-04-03
if you are on ubuntu, try from the konsole: "sudo apt-get install gparted" as Robin said.

---

### Post by mikewhatever on 2007-04-03
You'll need to shrink the one partition to get unallocated space on the HDD, then create the new partitions in that space. Gparted live CD is probably the best way to go.

---

### Post by laidback on 2007-04-03
Live Gparted will do nicely. It's great.

---

### Post by Lardadart on 2007-04-03
Thanks for all the help. I'm downloading gparted right now and I'm hoping for the best of course.

---

### Post by Lardadart on 2007-04-03
Gparted was the best. Again thanks for all the help.

---

### Post by theratwonder on 2007-04-03
Awesome. Glad to be of service :D

---

### Post by Patrick K on 2007-04-03
Any advantage using the Live GParted CD over using GParted on the Ubuntu Live CD?

---

### Post by laidback on 2007-04-05
Gparted on Live CD download is more up to date, i.e. later version. It formats memory sticks which the Ubuntu version doesn't appear to do. There are one or two other differences but I cannot quite remember what they are. Generally I have found it to be better.

---

### Post by Gina on 2007-04-05
From the website :-> The CD also offers the following programs: parted and fdisk
vi, ntfs-3g, partimage, testdisk, Terminal and Midnight Commander.
And also tool to make screenshots.If it's the same app, I used **testdisk** to repair a partition table which one of my Win apps decided to mess up after resizing a partition to grab space.  That was on **SystemRescueCD** another live CD.

I've found **gparted** the best partition editor too :)

---

