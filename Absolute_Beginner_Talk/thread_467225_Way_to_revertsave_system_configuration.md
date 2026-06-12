---
title: "Way to revert/save system configuration?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-07
I want to experiment with XGL and Compiz.  I know I could mess things up and would like a way to revert to my pre-XGL/Compiz system when things go bad.  

Any ideas?

---

### Post by indytim on 2007-06-07
Use Partimage and take a snapshot of your ops partition BEFORE you install the toys.  If things go south, use Partimage to restore the partition to the previous state.  This assumes you have more than 1 Lx ops present so you can boot to the alternative ops to restore your partition (you could use the install LiveCD and build in Partimage on a LiveCD boot also).

If this isn't the case, I thought I saw something posted a while back about a restore live cd that included a partimage as part of the live cd.  If this is what you need, stay tuned and perhaps someone from the collective can give you the name of the LiveCD I'm referring to.

Good Luck,

IndyTim

---

### Post by indytim on 2007-06-07
One other thing (duh), don't put the partimage snapshot of your ops on the same partition as your ops.....

---

### Post by aberadam on 2007-06-07
OK, great thanks.  I've only got one partition though...

---

### Post by southernman on 2007-06-07
[http://psychocats.net/ubuntu/partimage]("http://psychocats.net/ubuntu/partimage")

Aysui gives a good howto using the livecd. You'll have to install PI into your ram, but he walks you through it.

Not having but one partition, you can split the image into chunks small enough to fit onto a cd (I use CDRW media). Once you have your images, just burn them to cd and your all set.

---

### Post by aberadam on 2007-06-09
Great, thanks southernman.

---

### Post by southernman on 2007-06-09
Your welcome, aberadam.

---

