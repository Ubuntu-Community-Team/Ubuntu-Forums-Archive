---
title: "How can I free up space on /"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by jsast21 on 2008-04-11
I am running out of space on / and I cannot figure out why or where its going. When I use df -h, this is what I get:

jsast21@jsast21-laptop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.4G  3.9G  258M  94% /
varrun                982M  100K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
udev                  982M  116K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   34M  948M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5              20G  883M   18G   5% /home
/dev/sda1             201G   43G  159G  22% /media/sda1
/dev/sda3             6.9G  6.2G  709M  90% /media/sda3
/dev/sdc1             241M  103M  138M  43% /media/ALEXANDERSD
/dev/sdb1             970M  637M  333M  66% /media/ALEXANDER
jsast21@jsast21-laptop:~$ 


/dev/sda6 is my /root, sda1 and sda3 are my windows vista partitions.

Questions are, what could possibly be taking up so much room on /, how can I clear some free space, and is it possible/necessary to make this partition larger?

Thanks very much.

---

### Post by SOULRiDER on 2008-04-11
First of all, clear the cache of downloaded packages.
```
sudo aptitude clean
```

Also, you can use the Drive Viewer program thing (I cant remember the name since im running KDE) to see where all the space is being used in your disk.

---

### Post by jsast21 on 2008-04-11
Thanks very much. That took it down to 83%. I'm new at linux, does this look about right now?

jsast21@jsast21-laptop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.4G  3.4G  755M  83% /
varrun                982M  100K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
udev                  982M  116K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   34M  948M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5              20G  886M   18G   5% /home
/dev/sda1             201G   43G  159G  22% /media/sda1
/dev/sda3             6.9G  6.2G  709M  90% /media/sda3
/dev/sdc1             241M  103M  138M  43% /media/ALEXANDERSD
/dev/sdb1             970M  637M  333M  66% /media/ALEXANDER
jsast21@jsast21-laptop:~$ 


Out of 4.4G, 3.4G is being used on root. Is this where the install of Ubuntu is? Should it be around 3.4G for everything?  Can I make that partition larger by any chance? I've only had Ubuntu since Feb 08, and if its filling up that quickly I think I need more room.

One more question, how do you get the 'code' box on these posts?

---

### Post by NightwishFan on 2008-04-11
Uninstall the programs you do not want with synaptic.

---

### Post by jsast21 on 2008-04-11
Thanks - that took it down to 83%. I appreciate the help.

Still - how do you get the 'Code:' box in a forums post?

---

### Post by R6V2 on 2008-04-11
Press the code button when replying, note when using a fast-reply.

---

### Post by JoshuaRL on 2008-04-11
> **jsast21 said:**
> Thanks - that took it down to 83%. I appreciate the help.

Still - how do you get the 'Code:' box in a forums post?

Take the spaces out of the following tags:
[ code ]
sudo apt-get sample-code
[ / code ]

and you should get:
```

sudo apt-get sample-code

```

I don't think the tags are listed [here](http://ubuntuforums.org/showthread.php?t=726219) but there is a lot of good info for the forums.

---

### Post by jsast21 on 2008-04-11
Thanks much.

---

### Post by SOULRiDER on 2008-04-11
As someone mentioned, uninstall things you dont want.

The partition you chose is not too big really, you can resize it but it depends on how your partitions are set up. If I find a HOWTO on how to resize partitions ill post here :)

---

### Post by zvacet on 2008-04-12
You can resize partition using [Gparted live Cd](http://gparted.sourceforge.net/).Take some space from your home and that free space add to root.I think 10GB for root is enough.

---

