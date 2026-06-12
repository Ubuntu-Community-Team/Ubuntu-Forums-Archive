---
title: "Trying to set /home in new partition"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by frazelle09 on 2007-07-21
Have created and formatted a new partition, hda2.  In it i have copied my /home/frazelle files and want to use this as /home when i boot up.  My fstab has the 

UUID =some number /mnt/hda2 reiserfs comment=jiffymount,noatime,nodiratime,user,exec,dev,suid 0 0

line in it, but when i boot i get /home/home/frazelle which of course doesn´t work. 

 i´ve tried all kinds of combinations, but can´t seem to get this to mount as just /home/frazelle.  i now have /home/home/frazelle, /home_bak/frazelle and home_bak2/home/frazelle :confused:

What do i need to do to fix this blinkin business???  Am using Krusader as root to work with these directories and fstab.

Thanks for all the help! and have a great evening!  :)

---

### Post by vargasman on 2007-07-21
Try this [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by grishenko2000 on 2007-07-21
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

details how to move it to another partition. though it sounds like you've gone though most of those sets.
have you successfully mounted hda2 to /home/frazelle using the mount commands.

---

### Post by frazelle09 on 2007-07-21
i actually haven´t been using the ¨commands¨.  After creating the partition, i used Krusader to copy /home/frazelle to hda2.  This worked just fine.  It shows up under Konqueror as /mnt/hda2/home/frazelle.  Hmmm.... maybe all i need is /mnt/hda2/home /home (i think i´ve been using /mnt/hda2 /home).  i´ll try this and see what happens.

Thanks for the help!  and have a great morning!  :)

---

### Post by Irony on 2007-07-21
Your fstab entry should look something like this;

[PHP]/dev/hda2 /home reiserfs comment=jiffymount,noatime,nodiratime,user,exec,de v,suid 0 0[/PHP]

Note the *contents* of home should be copied into your hda2 partition (don't copy the folder itself). Your home folder will thus still be in root but its contents in hda2.

You don't have to mount home in /mnt or /media.

---

### Post by frazelle09 on 2007-07-21
Thanks guys!  That last one helped... use contents of home and not /home.  Now when i boot up i get 

root as an option and the one i´m looking for: frazelle, as well.  However when i click on frazelle, it looks like it´s trying to use frazelle, the screen goes black, a progress bar comes up and then disappears and finally the original screen comes up again with

root
frazelle

If i select root, i can login just fine.  When i check the file structure with Krusader, i can see that /home now has /frazelle under it so i guess it´s mounting alright.  The fstab entry is the same

/dev/hda2 /home reiserfs comment=jiffymount,noatime,nodiratime,user,exec,dev,suid 0 0

(i changed your ¨de v¨ to ¨dev¨.  i think that this is correct.  Is it?)

i wonder what i´m still missing...

Have a great morning!  :)

---

### Post by Irony on 2007-07-21
This might work;

[PHP]/dev/hda2 /home reiserfs defaults 0 2[/PHP]

If not you may have to use something along the lines of;
```

sudo cp -ax /media/hda1/home/* /media/hda2/home
```

to ensure an exact copy of home.

---

### Post by frazelle09 on 2007-07-21
Thanks, Irony!  Tried both, but to no avail.  i wonder what´s going on...  Uf, what a pain.  Well, will keep at it... and

Have a great afternoon!  :)

---

### Post by Irony on 2007-07-21
I assume you actually are using reiserfs and not ext3 which is the default for Ubuntu.

---

### Post by frazelle09 on 2007-07-21
Yup.  i´m actually running Freespire, but i figured ¨we´re all family¨, right?  :D

Have a great afternoon!  :)

---

### Post by frazelle09 on 2007-07-23
Well, finally able to get this set up.  i installed the beta 1.9.6 Freespire on the 1st partition and used this link, step by step, to set it up...

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Rebooted and, voila!  It works!  So, thanks again to all for your help and 

have a great evening!  :)

---

