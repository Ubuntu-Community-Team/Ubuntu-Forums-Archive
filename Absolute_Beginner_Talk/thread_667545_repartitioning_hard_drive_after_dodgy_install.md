---
title: "repartitioning hard drive after dodgy install?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by gruffwestern on 2008-01-14
Hi again,

  I used Wubi to install ubuntu for the first time last week, I played with it for about 2 days then decided to bin it, using add remove pro grammes in the window control panel, as ,the Wubi documentation advised.

  I thought nothing about this at the time as all appeared well with my restored XP machine, but after about a week or so, i longed for Ubuntu once more and decieded to reinstall it using the official method of downloading the live CD. again i had no problems..... except for the fact that that ubuntu can't remember my wireless key, but thats another thread..............

Sorry, i digress...................

  The problem is that now my 80 Gb HDD has been partitioned to a rather poor 20 Gb for windows and 40Gb for linux, when i only selected 20gb for the ubuntu install from the live CD. So to me it looks like Wubi did not remove the partition it created when i installed it previously?............ I hope you guys can follow this?!

I don't mind reinstalling Ubuntu and then re-installing it afterwards if that makes a difference...... I just want around 60 Gb for windows..........................for now at least!

Any ideas how i can do this?

---

### Post by dgray_from_dc on 2008-01-14
Try GParted.  With that you should be able to move, delete and/or resize parts of your hard disk.  You may have to do it from a live cd.  GParted can't move or resize a mounted volume.

---

### Post by logos34 on 2008-01-14
umm, wubi didn't create a partition...it runs inside windows.  

Boot frm the ubuntu live cd, 

>System>admin>gnome partition editor (or maybe it's now listed as simply 'Partition editor')

Delete the ubuntu partitions.  Resize/expand XP to the desired size.  

Click on the install icon.  Choose 'Guided' -- 'largest continous free space'.  That should pick the empty disk space.  If not go back and select 'manual'.  You need an ext3 / (root) and /swap.

edit: looks like dgray beat me to it.

---

