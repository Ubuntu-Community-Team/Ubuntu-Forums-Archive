---
title: "No internet nor drive"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-13
Alright so now I have my laptop dual booted with Ubuntu 6.10 and Windows XP, thanks for all your help!

But now when I'm in Ubuntu it doesn't connect to the Internet. When I went into the terminal and entered ifconfig it gave the internal IP (127.0.0.1). I don't know if it's something weird Dell has going on ethernet-wise? (Because unlike my desktop, which I built, the laptop is a Dell from the "Dude, you're getting a Dell" era).

My other question is more XP-ish. When I partitioned my laptop hard  drive (40 gigs) the result ended up being 15-XP, 15-Ubunutu, 1-Swap and the rest is supposed to be FAT32 shared. The shared region was formatted using GParted, and Windows doesn't recognize it. Thoughts?

P.S. I love this guy: ](*,)

---

### Post by dbbolton on 2006-11-13
are you using eth0 or eth1 ?

---

### Post by nonpareilpearl on 2006-11-13
eth0 I believe

---

### Post by dbbolton on 2006-11-13
did you try going to
system > administration > networking

and making sure that all the settings are correct?
----

also, did you try running a partitioning tool on windows like swissknife or whatever it's called

---

