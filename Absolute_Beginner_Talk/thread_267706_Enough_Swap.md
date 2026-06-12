---
title: "Enough Swap?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-09-29
Can someone fill me in on the term Swap Space?

Also, i have 512MB RAM, isnt that for swapping & temp storage?
But i have also assigned 2GB of Swap Space, is that enough?

---

### Post by po0f on 2006-09-29
Captain Kirk76,

It used to be recommended that you have two times the amount of RAM you have reserved for swap.  Today's machines with multi-gigabyte RAM configurations are moving away from that, but disk space is cheap so why not.  Two gigs is plenty if you have 512 MB RAM.

If this is a laptop you are talking about, you will defintely want to keep your swap space if you intend to suspend-to-disk, as your swap space is used to write memory to.

[EDIT, didn't explain swap]

Swap space is used if you run out of real memory.  Your computer will respond a little slower, since disk access is way slower than memory access, but at least your computer won't crash.

---

### Post by hyper7 on 2006-09-29
Swap space contains mainly partition information.  you don't need a crapload of it.  2GB is more than enough. Depending on how many operating systems and how quickly you like to boot one iin particular, you may want to give more swap space to one over the other.

256 is normal and is plenty.. I can't see why you'd need more than that.  Then again, I'm a newb answering big boys questions.

---

### Post by Captain Kirk76 on 2006-09-29
Thankyou for your (speedy) reply!
the computer in question is a 2 year old PC running at 1.8GHZ & 512RAM.

So 2GB Swap should do me just fine?

EDIT: The PC also has Windows XP consuming the other 4 Partitions. all in NTFS, so Linux wont write to them, Linux only has two partitions, the Swap, and the main one.

---

### Post by hyper7 on 2006-09-29
Eeek, spoke too soon.  Swap files should be proportional to diskspace.  I've no idea what the ratio is.

I lost.. :neutral:

---

### Post by po0f on 2006-09-29
Captain Kirk76,

Yes, two gigs swap is plenty.  If you need more than that, you might want to look into upgrading your memory.  If you're at all worried about the performance loss when swapping (when gaming, for instance), a memory upgrade is highly recommended.

---

### Post by Captain Kirk76 on 2006-09-29
well if it helps, my Main HDD is 250GHZ, my secondary is 80GB, so 330GB total. Though Linux only has about 30GB of that. the rest in eaten up by XP's 4 partitions.

---

### Post by Captain Kirk76 on 2006-09-29
Thankyou for your replies all!

---

### Post by Drakkor on 2006-09-29
Think it's supposed to be twice your memory,so like I also have 512mb memory,my swap is a tad over 1G.
Edit: lol Kirk,never heard of a 250GHZ HDD,lol :p

---

### Post by sbergman27 on 2006-09-29
> **Captain Kirk76 said:**
> So 2GB Swap should do me just fine?

I'm usually pretty liberal with swap, though most of it goes unused.

However, one place where you *do* need enough is on a laptop if you want to 'hibernate', aka suspend to disk.  There, you do in fact have to have, I believe, swap = 2 x ram.

1GB should actually be fine for 512MB.

---

### Post by _duncan_ on 2006-09-29
I read somewhere that a good rule of thumb is to assign 1.5x your RAM size. So for 512MB it should be in the vicinity of 768MB.

I also have 512MB RAM. I remember Ubuntu Breezy defaults to 800+MB swap space if asked to auto-partition my hard drive during installation, so the 1.5x rule of thumb is not too far off.

Your 2GB swap space is more than enough.

BTW, the M$-Window$ equivalent of swap space is the pagefile.

---

