---
title: "dual-boot partition question"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2006-12-11
Hello.

I'm looking to set up Umbuntu on a dual boot with my Windows XP. My hard drive is 80Gig and is currently one big 80gig partition. I was reading this page for help on installing the dual boot:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The part that got me concerned was this statement when Gparted is started:

*You'll then be presented with three options. This first option is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up. **Ubuntu will automatically shrink your Windows partition and create a new Ubuntu partition out of the free space.** *

The part about automatically shrinking my Windows partition has me wondering how much shrinking are we talking about? How does the gparted program determine how much of my 80 gig should go to Windows and how much to Ubuntu? I don't want to lose much of my Windows space as Ubuntu is just an experiment for the time being until I decide if I should keep it (in which case I'll go 100% Ubuntu) but I don't want to try Ubuntu to the detriment of my daily Windows computing usage.

The other alternative is to manually try to partition with this gparted program however I am completely new to this and the instructions seem unclear, at least to me, so I'd rather have the program do it automatically for me. I'm just nervous Umbuntu will get more HD space then it needs and mess up my Windows partition.

Any help or advice appreciated.
Thank you.

---

### Post by igknighted on 2006-12-11
If you select that option it should give you a slider to choose exactly how much to shrink off of windows.  I've never done it with a windows partition, but thats what it always gives me for shrinking my linux partitions.

---

### Post by atarileaf on 2006-12-11
Thanks for the quick reply. It was the part that said that it would "automatically" resize my partitions that had me concerned, as if to say Windows would be shrunk down to the minimum possible to allow maximum space for Ubuntu.

---

### Post by kiwidipstick on 2006-12-11
Hi, as igknighted says, just use the slider to reduce the size of the windows partition. I have done this and it worked fine for me.By sliding the slider you control how much shrinkage you need. kiwidipstick:-D

---

### Post by atarileaf on 2006-12-11
Thanks again. Very helpful and friendly community here. :D

---

