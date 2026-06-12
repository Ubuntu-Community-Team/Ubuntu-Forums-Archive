---
title: "Uninstall completely"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by nmcvicar on 2008-01-20
Some months ago I installed 7.04 (dual boot with XP).

I like Ubuntu but the install is somewhat botched and I can't install updates of any kind. 

With guidance I've found on this forum I've tried to fix it but it hasn't worked out. I give up. I just don't have the time to keep trying to sort it out. 

I want to remove Ubuntu completely and restore my MBR.

How do I do this?

Thank you,
Neil

---

### Post by mnemosyne on 2008-01-20
You could use [GParted]("http://gparted-livecd.tuxfamily.org/index.php") to delete the Ubuntu partition. That should do it.

---

### Post by Paul820 on 2008-01-20
If you have your windows disk you can put the disk in and go to recovery mode from the options, then type:
> fixmbr
If you don't have the windows disk then you could use the supergrub disk or see this link [http://www.arsgeek.com/?p=3340]("http://www.arsgeek.com/?p=3340") to use an ubuntu live cd to do it for you. After you have fixed the mbr then from inside windows you can delete the partition with the device manager,( i think it's called that but i have not used windows for a long time so someone correct me if i'm wrong ) and then redistribute the space between the partitions you have kept.

---

### Post by mdpalow on 2008-01-20
Before giving up... why not give it one more chance, but this time install a clean copy of Ubuntu 7.10. Try to have a cat5 cable plugged in, so you are connected to the Internet if/when you decide to try it.

I think you might just have a lot of things fixed for you right from the beginning. The install only takes me 12 minutes on my computer, so if you can give yourself 30 minutes at most for everything (updates, etc..) at least you'll know you gave it one last worthy attempt. :)

I install 7.10 w/ cat5 plugged in and everything works out of the box. Then I take out cat5 and put in my WEP password and wireless works...

Try it if you haven't already and good luck to you with whatever you ultimately decide...

---

### Post by nmcvicar on 2008-01-20
Thanks to all,

MDPALOW, 

I've tried and tried with help from people on this forum. Nothing has worked. I can't install even one update. 

I resent it but .... back to Windows I go. I'll need a RAM upgrade. *$#!

N

---

