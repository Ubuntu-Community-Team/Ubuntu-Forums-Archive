---
title: "Partitioning Situation on a MacBook"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by shadowofgrael on 2010-10-13
I am trying to install Meerkat on my macbook. I have already received  some assistance from the Apple Forums and LQ but would like to ask the same question of people who have most likely dealt with this problem before, confirmed ubuntu users on Apple machines.

Apple Thread: [http://discussions.apple.com/thread....13432&tstart=0]("http://discussions.apple.com/thread.jspa?threadID=2613432&tstart=0")
LQ Thread:[http://www.linuxquestions.org/questions/showthread.php?p=4126580#post4126580](http://www.linuxquestions.org/questions/showthread.php?p=4126580#post4126580)

Original Post: <I am on a black mac book, late 2007 I believe, and am dual booting Snow  Leopard and Ubuntu 10-4. Very recently I installed rEFIt "manually". In  an attempt to upgrade to Ubuntu 10.10 I encountered several errors (I  suspect disk drive problems) and ultimately made no progress. In an  attempt to make things simpler I decided to remove the initial Ubuntu  installation and add the new one. 

Under Disk Utility, I can neither remove Ubuntu's partition nor the Swap  space. The error I receive says "Mediakit reports no such partition."

Though solutions to my entire problem would be nice, I am really only  interested in getting a clearer picture of what exactly is going on. I  want to know:
1: what is mediakit, why it is in error and how to fix it.
2: what else have I unknowingly screwed up (if anything)
3: how do I avoid this situation (mediakit issues) in the future (I have had the same issue in the past).         

                                                                  macbook                                                                                           Mac OS X (10.6.4)                                                                                                                                                                                       >

---

### Post by pc_michael on 2010-10-13
Mac OS X  (via mediakit) is unable to read or manipulate Linux partitions such as Ext3/4 or Linux Swap, so you won't be able to do anything via Disk Utility.

The way to do this is to boot from your Ubuntu LiveCD and use GParted (Gnome Partition Editor) to remove the Linux partitions and create the new ones when you start over.

Good luck!

Edit: If you don't want to use the Ubuntu LiveCD, you can also download an ISO of a bootable GParted CD [directly from their website](http://gparted.sourceforge.net/).

---

### Post by shadowofgrael on 2010-10-13
Thank you for the clarification.

---

