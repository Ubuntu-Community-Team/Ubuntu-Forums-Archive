---
title: "[SOLVED] Can I use Gparted 'after' I have installed Ubuntu?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-10
Is it safe for me to repartition my HDD with GParted after it has already had Ubuntu installed?

Also will the necessary files be moved into the new partition HOME ?

What I planned on doing was making 

/ = 10GB
/Home = 28GB
SWAP = 1GB

OR do I need to a new installation ?


[img]http://i16.tinypic.com/4pezev6.jpg[/img]

---

### Post by shae on 2007-09-10
The worse that could happen is the destruction of your root partition.  On a new install, all this would mean is having to reinstall.  However, if you have done any important work on this computer, you should back it up.  Generally speaking you should back up anything important when you go about resizing partitions.

---

### Post by bodhi.zazen on 2007-09-10
Yes, you can resize after installing ...

You should resize from a live CD and you may need a newer version of gparted, as is found on gutsy or the gparted live CD.

---

### Post by 1oki on 2007-09-10
sure you can!! If you ruin your root partition, just reinstall the root and keep your home (do not format your "home" so you save all your documents and what not). I did that a few times! Amazing how simple it is to restore your system that way!

---

### Post by rsambuca on 2007-09-10
Like everyone says, you can resize the partition using the liveCD (since you can't resize a partition while it is mounted).  You can then create a new partition for home in the empty space created.  You will then have to transfer your /home folder to the new partition and then edit your fstab accordingly.

---

### Post by bodhi.zazen on 2007-09-10
Sorry , I mis-red your post.

See this link to move /home to a separate partition :

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by chrome307 on 2007-09-10
OK thanks for letting me know :)
[B]
[EDIT][/B]

[IMG]http://i13.tinypic.com/6eyj0x5.jpg[/IMG]

---

### Post by bodhi.zazen on 2007-09-10
Looks fine ...

You need to move your home partition ... See the first link I gave you or you can look at this one as well (same basic information)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you re-install you need to select sda2 as /home

---

### Post by chrome307 on 2007-09-10
I have read that tutorial and there are some typos in the commands posted :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Also using the mount mkdir command I end up with a large filename for the second partition ....  ' media/mount/......... ' 

What I realised was that when you use the Ubuntu LiveCD to manually create partitions, it allows you to mount each one at a specific point  ie ROOT  and HOME.

So my hda1 would be mounted at ROOT (Primary)
 ....      hda2 would be mounted at HOME (Logical)

Using Gparted this does not allow me to make these choices.

It most probably is me not being able to understand and follow the instructions fully.

In the interim I have moved back to a similar setup as before

[IMG]http://i11.tinypic.com/4umoyl3.jpg[/IMG]

---

### Post by bodhi.zazen on 2007-09-10
I think we are getting mixed up a little ...

Partitions can be primary of logical, that part does not matter ...

A physical partition is /dev/xxx (/dev/hda1 or /dev/sda1)

You mount the partition at the mount point ...

ROOT is / ; same as C:\

so ...

/dev/sda1 is mounted at /
/dev/sda2 is mounted at /home

Once you make a new partition to become your new /home, follow that how-to to move your HOME from the /dev/sda1 to /dev/sda2 

Which command are you having a problem with ?

---

### Post by chrome307 on 2007-09-11
I think in this instance I will simply leave it alone and wait for the new release of Ubuntu.

This way I will simply format the HDD again manually and set it up using the LiveCD.

What concerned me was that after the 1st attempt at partitioning, the 2nd partition had 500mb of files on there ..... I had assumed the 1st partition ( 10GB) would have been large enough to contain all the existing files and not have to carry over 500MB into the 2nd partition.

Thanks for your help anyway.

---

### Post by BLTicklemonster on 2007-09-11
Bear in mind that every time you format, your partition will change it's name. At present, I think you said it was HDA2, next time it will be HDA4 because swap has HDA3 already. At least that's what mine always does. I'm up to HDA7 as / now, lol.

---

### Post by chrome307 on 2007-09-11
OK - I decided to have one more attempt of it just to make sure and it was successful this time around :)  

For other members, do not follow the instructions in the 1st link use the instructions provided by Psychocats instead:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[IMG]http://i14.tinypic.com/6h3ybtw.jpg[/IMG]

---

### Post by BLTicklemonster on 2007-09-11
Psychocats rocks anyway, so that's good advice.

---

