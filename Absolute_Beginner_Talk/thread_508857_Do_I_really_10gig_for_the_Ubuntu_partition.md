---
title: "Do I really 10gig for the Ubuntu partition?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Nudgeworth on 2007-07-24
Thank you Guys, for answering my questions :)

Hello, complete noob boy here.
 
 I'm planning to set up a dual boot system. And I'm planning have all of the media file s in a partion of their own to protect them.
 I've seen recommendations that partition containing Ubuntu should around 10 gig.
 Does it need to be this big if the media is stored in another partition? T

---

### Post by Rocket2DMn on 2007-07-24
You could get away with less, it just doesn't leave a lot of room for expansion.  6 gigs would probably be enough, but it depends on how much flexibility you want.  I've seen people run on 4 gigs, but they tend to run out of space.
What do you mean protect your media files?

---

### Post by doomster on 2007-07-24
you will probably need about 3gb for a full starting  install of ubuntu. 10gbs are recomented, to give you the free space to install other software inside ubuntu system.in my honest opinnion the more you can give the more you get from ubuntu,  :D

---

### Post by punx45 on 2007-07-24
back when I had a separate /home partition i had / at around 10GB and it got to over 80% capacity relatively quick.   I would say if your disk is over 100GB give / more space.

---

### Post by sd.chen on 2007-07-24
The documentation says that a regular Ubuntu install takes up about 3 GB, and any extra applications you install usually goes on that partition as well (for example I have MATLAB installed on /usr/share taking up just over 500 MB).

---

### Post by punx45 on 2007-07-24
> **Rocket2DMn said:**
> 
What do you mean protect your media files?

my guess is he probably means that if the OS gets FUBARed he can reinstall over / without wiping out his media files.

---

### Post by Rocket2DMn on 2007-07-24
> **punx45 said:**
> my guess is he probably means that if the OS gets FUBARed he can reinstall over / without wiping out his media files.

Fair enough - just remember it doesn't help you if the drive physically kicks the bucket.  Also, if you're dual booting you could easily recover your files from the Ubuntu partition with the driver that enables Windows to read ext2/3 file systems: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Nudgeworth on 2007-07-24
To ROCKET2DMN: A friend tells me it's a good Idea incase something Catistrophic happens an operating system.

 Hmm and I understand the logic in in Allowing for the expansion of Ubuntu, unfortunately, I have Vista which I wish to keep :roll: and I only have a 80 gig drive lol

---

### Post by doomster on 2007-07-24
i dont believe that vista installation requires more that 4GB... not to say 70 :) 
so i thing a 9GB space and 1GB swap spared for the Ubuntu experience, is 
just a small tribute.
      to be honest, i believe that after a month of dualbooting or so, you will not
have such problems... by the time you manage to work compiz-fusion program,
you will destroy windows partition, and enlarge ubuntu partition to fully cover
your hard disk drive :D:D:D

---

### Post by Nudgeworth on 2007-07-24
also, how large should I mafe my swap partition? 
 I have a Celeron 1.7 Ghz  and 512 ram.
 
 About 1.5gig?

 Edit: Notices doomsters post. Hmm so Ubuntu can become like a virus infection on my harddrive lol

---

### Post by Rocket2DMn on 2007-07-24
> **Nudgeworth said:**
> To ROCKET2DMN: A friend tells me it's a good Idea incase something Catistrophic happens an operating system.

Indeed, also please note my above post.  I would also suggest investing in a second (external, perhaps) hard drive for backup.  You can get them pretty cheap, and you only have to need it once for it to be more than worth it!  There is autobackup software for windows and for linux that expedites the task.  Enjoy :)


SWAP: A gig should be plenty.  If you foresee a RAM upgrade in your future, then maybe 1.5.

---

### Post by doomster on 2007-07-24
> **Nudgeworth said:**
> also, how large should I mafe my swap partition? 
 I have a Celeron 1.7 Ghz  and 512 ram.
 
 About 1.5gig?

i think about 1gb of space should be enough

---

### Post by bodhi.zazen on 2007-07-24
> **doomster said:**
> i dont believe that vista installation requires more that 4GB... not to say 70 :) 
so i thing a 9GB space and 1GB swap spared for the Ubuntu experience, is 
just a small tribute.
      to be honest, i believe that after a month of dualbooting or so, you will not
have such problems... by the time you manage to work compiz-fusion program,
you will destroy windows partition, and enlarge ubuntu partition to fully cover
your hard disk drive :D:D:D

9 Gb ~ LOL

> 1 GHz 32-bit (x86) or 64-bit (x64) processor
512 MB of system memory
20 GB hard drive with at least 15 GB of available space

I presume they need 5 Gb of free space for a swap file of some kind :???:

---

### Post by stchman on 2007-07-24
> **Nudgeworth said:**
> Thank you Guys, for answering my questions :)

Hello, complete noob boy here.
 
 I'm planning to set up a dual boot system. And I'm planning have all of the media file s in a partion of their own to protect them.
 I've seen recommendations that partition containing Ubuntu should around 10 gig.
 Does it need to be this big if the media is stored in another partition? T

A fully stocked Ubuntu runs around 3.5 and the swap partition runs around 2.  So that is near 6.  Unless you are really strapped for hdd space give Ubuntu at least 15GB not including swap.

---

### Post by atlfalcons866 on 2007-07-24
i put ubuntu fiesty on a 2.6Gb hard disk before and only had like 74MBs left though

---

### Post by dkaddict on 2007-07-24
10GiB /home
10GiB /root

are plenty to start with. I would have filled a 10gig /home partition after a month or so though so try get as much space as u can for that. I don't recall ever using 10gig in my /root partition.

dk

---

### Post by Nessa on 2007-07-24
lol I have a 20GB partition for Ubuntu. I don't want to adjust the partitions again so I'll keep it and just make the most out of it. It's fun tinkering with Ubuntu. I can't say the same for XP. I'm almost afraid to install anything new fearing it would crash again.

---

