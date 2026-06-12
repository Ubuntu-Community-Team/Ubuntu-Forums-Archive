---
title: "Can I dual boot use a clone image?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by crazyoldman on 2008-03-29
Hi all. I've returned to Ubuntu after a trying it out for a brief period a couple of years ago. My Vista installation crashed and burned, and I was having problems with my hard drive, so I thought I might install Ubuntu and give it another test drive. So after a few days I've installed compiz, AWN, sorted my themes, Nvidia drivers, sound card, media codecs, bitttorent etc. I've learnt a few terminal commands, and I actually prefer the look and feel of Ubuntu now. The compiz cube is excellent!
My problem is this - Lenovo are sending my a new hard drive next week, (Seagates seatools told me there was damage to it), along with the rescue and recovery DVD for my previous install. I really want to have a dual boot Ubuntu/Vista system, but don't want to spend ages setting up Ubuntu again. So I have a number of questions.
1. Can I set up a dual boot installing from a clone of my present setup?
2. What is the best package to use to clone the Ubuntu Installation?
3. Am I better off to start from scratch with fresh install of Ubuntu? If so, would I be better off to wait for the stable release of Hardy Heron?
Any advice will be gratefully received. 
Also I got Mrs crazy a MacBook yesterday - she knows how to use Leopard, so now I guess I'll have 2 new OS's to learn!!
Heres a pic of my current setup for those desktop decoration afficiandos out there:

[ATTACH]64234[/ATTACH]

[ATTACH]64235[/ATTACH]

[ATTACH]64236[/ATTACH]

---

### Post by Berean on 2008-03-29
[QUOTE=crazyoldman;4610630]
1. Can I set up a dual boot installing from a clone of my present setup?
2. What is the best package to use to clone the Ubuntu Installation?
3. Am I better off to start from scratch with fresh install of Ubuntu? If so, would I be better off to wait for the stable release of Hardy Heron?

1. You shouldn't have a problem.  Presumably you'll have Vista already installed and then you'll just set up a new partition.
2. I use partimage.  Don't be fooled when you install it: I didn't find anything!  However, afterwards if you simply type "partimage" (NOTHING else) in Terminal you get the GUI come up and then you just enter the details you want.  Prior to this I partitioned my hard drive.  Also, I don't dual boot anymore, so I partitioned my external hard drive using Partition Editor, and then made a disk image using this thread:
[http://ubuntuforums.org/showthread.php?t=725269](http://ubuntuforums.org/showthread.php?t=725269)
3. I think it's good practice to do a fresh install, but it depends how heavily you've modified your system.  Hardy Heron will have a greater ability to "see" hardware and drivers etc. but if you've got Gutsy as you'd like it there's no reason to change (other than perhaps additional security).  If you do install Hardy, wait a month and then do so: problems will have been ironed out by then. 

Alternatively, if you don't want to save to an external hard drive, and just copy an image see this thread:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Hope this is of some help.  Regards.

---

### Post by crazyoldman on 2008-03-29
Cheers!! I think I'll try both methods you mentioned to be on the safe side.

---

