---
title: "partition question"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by gene74 on 2007-07-10
im finally ditching windows on my home machine, how do i partition my hd. its a 160 gb hd.
i tried to find the post i saw, it said like for the swap, 2x the size of your ram. I have 1gb of ram and thats all i remember. TIA

---

### Post by mikewhatever on 2007-07-10
20 GB --> root
2 GB ---> swap
The rest of space --> /home

---

### Post by Sparkster185 on 2007-07-10
I second the above poster.  Honestly, 20GB at / is more than enough.  My / partition is still under 5G and I've been using Ubuntu for 10 months now.

It's also a great idea to separate your / and /home partitions, so if you re-install your OS you don't loose any data.

---

### Post by az on 2007-07-10
Just take the default guided partitioning.  You do not need anything more than a / and a swap partition.  The installer will calculate the sizes for you.

If you want to do manual partitioning, go ahead, but there is no advantage to doing so.

---

### Post by st0nes on 2007-07-10
I disagree with az -- there is a huge advantage to having /home on a separate partition: you can do a reinstall of Ubuntu from CD without losing any data from /home if you manage to bandex the OS.  This is essential if you are ever going to test new versions before release.

---

### Post by taffy-nay on 2007-07-10
It all depends on how you want your system to be setup.

By default Ubuntu will create and install on one large partition.

It is generally good practice to keep your home partition seperate. This helps to preserve your data in the event of faliures

---

### Post by az on 2007-07-10
> **st0nes said:**
> I disagree with az -- there is a huge advantage to having /home on a separate partition: you can do a reinstall of Ubuntu from CD without losing any data from /home if you manage to bandex the OS.  This is essential if you are ever going to test new versions before release.

Actually, that's the best way to screw up your user configurations.  A future version of an app may bork the configurations for a past version - it's not a good idea to share a home directory with mixed versions of apps.

As far as losing data, it's easier to do a backup the conventional way.

> **taffy-nay said:**
> 
It is generally good practice to keep your home partition seperate. This helps to preserve your data in the event of faliures

It's better to do a backup the conventional way.  If you think your seperate partition is safe from a drive failure, you are wrong.  You should still back your data up to another disk or another medium.

/home drive on a seperate partition was a good idea a few years back, when you didn't run a lot of desktop apps and backup media was expensive.  This is no longer true.  It's a fun experiment, but I would not recomend it as a partitioning strategy for the everyday user.

---

### Post by sugarland2k on 2007-07-10
I keep a normal home folder and a backup partition.  I backup data from /home to /backup.  This keeps you data and those hidden setup files used in Ubuntu/Kubuntu but you can have a backup when needed.  I use my /home data for both Kubuntu and Freespire

Friends don't let friends run Vista!

---

