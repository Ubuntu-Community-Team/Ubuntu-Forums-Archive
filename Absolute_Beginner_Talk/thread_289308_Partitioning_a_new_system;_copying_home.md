---
title: "Partitioning a new system; copying /home"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-10-30
I'm planning on getting a notebook soon, which will be a pure Ubuntu system (most likely Dapper; Edgy if I manage to download it), and I'd like to ask around for the best (or most practical) way to partition it.

The system I'm eyeing comes with 60GB HD and 512 of RAM (might bump it up to 768 if budget permits) so I'm thinking:
[LIST]
[*]1GB for swap
[*]20GB for /home
[*]39GB for /
[/LIST]

This will be a single-user notebook, mostly for schoolwork (presentations, reports), and maybe playing Diablo 2 if I amange to download WINE on my dial-up. (but if my mom asks it's only for schoolwork!) :mrgreen: 

Also, is thre a way to copy my existing /home (on my desktop) to the new sytem? Not realy important, but it would mean less set-up time. Mostly the fonts, OOo prefs and my firefox profile- though I *could* just copy those.

---

### Post by aysiu on 2006-10-30
You can copy your existing /home with PartImage. If it's not already on a separate partition, you can move it to one.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

By the way, any reason you want to make / so big and /home so small?

---

### Post by eilu on 2006-10-30
> By the way, any reason you want to make / so big and /home so small?

Is it supposed to be the other way around? :confused:

---

### Post by po0f on 2006-10-30
eilu,

I currently have / (root) partitioned for 25G of space, and only 10% of it is being used (I also have separate /home, /var, /tmp, and /usr/local partitions though).  With only the separate home partition, usage of my root partition would be around 26%.  You could easily get away with making root a 15G partition.

And since this is a laptop you are wanting to install Ubuntu on, make sure swap *at least* equals the amount of RAM you have if you want to suspend-to-disk.

[EDIT]

Spelling...

---

### Post by schwascore on 2006-10-30
Your /home partition should contain the bulk of your personal data, so usually it is the larger of the two partitions.  The only reason / should be larger than /home is if you require a HUGE amount of software.  My laptop only has a 30G hd but my partition table is as follows:

swap  1GB
/     8GB
/home 20GB

---

### Post by aysiu on 2006-10-30
> **eilu said:**
> Is it supposed to be the other way around? :confused:
Even if you installed a lot of programs, I can't imagine your / partition getting bigger than 8 GB. With Xubuntu, Kubuntu, and Ubuntu installed (and some other programs), mine is about 3.5 GB.

Your personal data, however, can get huge (music, pictures, movies, documents).

---

### Post by eilu on 2006-10-30
ah, I see. Hang-over from Windows I suppose :) 

so I guess 10GB for / is more than enough, so would this be better:
10GB for /
1GB for swap
49GB for /home

what is suspend to disk?

---

### Post by aysiu on 2006-10-30
Yes, that's a much better partitioning scheme.

---

### Post by zetetic on 2006-11-21
aysiu said:
You can copy your existing /home with PartImage. If it's not already on a separate partition, you can move it to one.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Correct me if I'm wrong, but I don't think method 1 ([http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)) will work in case both partitions (source and destination) are encrypted.

And it takes only one unencrypted partition to bring the data completely unsafe and unprotected...

regards,
zetetic

---

