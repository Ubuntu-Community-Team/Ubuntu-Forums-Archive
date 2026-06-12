---
title: "Best FS for pure storage?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-10-15
I know there's a ton of debates over file systems (I don't mean to start any of those). On my desktop, I have a 15GB hard drive and a 160GB hard drive. The 15GB holds my OS and is ext3 (I just stuck with the default). But I'm going to use the 160 as pure storage - documents, music, and movies. No programs, no operating systems, nothing but "stuff." 

Is there a particular file system that would work best for that? I know having two different file systems on two hard drives works, but does it inhibit performance at all?

I have it as XFS for the time being, but I have hardly anything on there, so it would be nothing to backup and switch.

So, no flamewars, but what would be the best FS for data storage interacting with an ext3 OS?

Thanks,
Tony R.

---

### Post by PriceChild on 2006-10-15
Well if you're going to be doing it for pure backup and storage, and only with an ext3 OS.... why not just ext3.

Unless you're really REALLY looking for EXTREME performance, i can't see the point in you needing to research that much about it?

---

### Post by Kateikyoushi on 2006-10-15
Well I tried several FS depending on what was the purpose of that partition.
XFS is better with big files JFS with smaller, reiser is slightly better than ext3 (some might say with tweaked ext3 they matched it).

Because you mix small files docs and big ones films you can even stick with ext3.

Honestly I do not think it has real merits other than experience if you switch.

---

### Post by bodhi.zazen on 2006-10-15
I agree with PriceChild and would stay with ext3

---

### Post by Lord Illidan on 2006-10-15
Aye, ext3.. can be read with windows easily with a driver..and compat with all distros.

---

### Post by zitch on 2006-10-16
From my own reading and a bit of my own experience, Ext3 seems to be the least problematic for people.  For example, I ran XFS on my laptop for my home partitions, and I often hit on the "zeroed out file" problem when the laptop locks up when shutting down (Damn you ATI!).  I do plan on backing up my home drives at some point and reformatting that partition as ext3.  On the other hand, on my file server with a battery backup, I'm running XFS on it and haven't had a problem with it yet.

ReiserFS, I've heard horror stories of entire filesystems being corrupted in the past, but it seems those problems have largely been fixed.  It is much newer than the other systems, so it might be good to give it time to mature.  I haven't heard too much about JFS, though.

So, yeah, for the least amount of problems I do recommend Ext3 like the others.  It seems to be the most stable filesystem on Linux right now, though it might not be the fastest.

---

