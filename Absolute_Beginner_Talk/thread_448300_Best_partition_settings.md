---
title: "Best partition settings?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by rodrigo juarez on 2007-05-19
I screwed my Edgy installation. So I'm going to install Feisty from scratch and I was wondering what could be the best partition settings to use.
I've read that it is convenient to have swap, root and home partitios. Also, I've heard people saying we should have a partition for temp (he said because temp tends to eat up too much space).
I have a 80 GB hdd so I could guess something like:
2GB for swap (at the beginning of the drive, the faster sectors)
20GB for / (next to the swap partition)
58GB for home ('til the end of the drive)

I'm not making any partition for temp.
Would this be OK?
Is enough space for root?
Would be swap ok at the beginning of the drive?

Thanks for your help.
=D

---

### Post by freebeer on 2007-05-19
Your proposed layout seems to be in accord with the general consensus.  That's basically how mine was set up.  I used the same arrangement on another machine, and when I installed Feisty on it, the installation was very smooth... it didn't touch /home at all, so that was a time saver.  :)

I don't know about having /swap as the first partition, but I don't know that it matters.  I think the 20 gigs for / is fine... that's what I went with.

---

### Post by rodrigo juarez on 2007-05-19
Thanks for your reply.
> **freebeer said:**
> it didn't touch /home at all, so that was a time saver.  :)

You mean recovering root? because i've just erased my drive (It was overwrote, however) so I will need to create home again.

---

### Post by sandman55 on 2007-05-19
Generally swap is twice your RAM

---

### Post by rodrigo juarez on 2007-05-19
Ok, so it should be 2048 instead.
Would it be ok at the beginning of the drive or it just doesn't matter?
thanks.

---

### Post by rodrigo juarez on 2007-05-19
Anyone else?
plis?

---

### Post by pebo on 2007-05-19
Don't think it matters but I may be wrong. I don't think you need that much swap space though - 1 gig should be plenty on a system with plenty of RAM

---

### Post by tchoklat on 2007-05-19
If you choose to partition your drive automatically with the liveCD the swap will be placed at the end of the drive. So that is what I did. Your /home will contain your data so should be large. Your / need only be as big as Ubuntu installation. 20 Gb is more than enough. Swap should be twicer Ram but not more than 2Gb.
 
thcoklat

---

### Post by rodrigo juarez on 2007-05-19
Thanks for your help.
We should porst a in-deep guide to partitioning somewhere.
=D

---

### Post by pebo on 2007-05-19
[Here's]("http://www.psychocats.net/ubuntu/partitioning") a simple / useful guide to partitioning

---

### Post by Inxsible on 2007-05-19
My partitions are as follows

/ 5 GB
/home 20 GB
/swap 980 MB (although i wanted 1  GB, somehow the bytes got screwed up while assignment and this is all i was left with when swap's turn came ;) )

i also have /shared of about 72 GB where i have my music which i sahre with my vista dual boot.

Rest 50 GB is Windows Vista and its installation.

Now, however i think 50 GB is too much for windows that i have hardly used since i installed Ubuntu. So i think i might increase / (root) by 10 GB adn decrease Windows by 10 GB

---

