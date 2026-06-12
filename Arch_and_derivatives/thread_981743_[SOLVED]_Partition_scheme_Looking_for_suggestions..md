---
title: "[SOLVED] Partition scheme: Looking for suggestions."
date: 2008-11-14
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-11-14
I've installed many distros in the past and as a result my current partition layout is, well, out of order. Now, I just want to keep Arch and nothing else. 

I'm going to format and restructure as below:

HDD: 100 GB, RAM: 2 GB
```

/         10 GB      as JFS
/var      2 GB       as ReiserFS
swap      2 GB     
/home  <remaining>   as JFS

```

Is the partitioning scheme OK? Is the order really important? Thanks in advance for your suggestions.

EDIT: Thanks everyone who replied. I'm currently planning to do the following. 

```

/         10 GB      reiser
/boot     500 MB     ext2
swap      2 GB     
/home  <remaining>   as JFS

```

---

### Post by handy on 2008-11-14
Do you ever use your /swap?

I have only 1Gb of RAM in the iMac, & I don't have a /swap partition these days.  I don't need one.

My other machine has 2Gb of RAM & I never use a /swap on any distro's that go on it either.

---

### Post by kpkeerthi on 2008-11-14
> **handy said:**
> Do you ever use your /swap?

I have only 1Gb of RAM in the iMac, & I don't have a /swap partition these days.  I don't need one.

My other machine has 2Gb of RAM & I never use a /swap on any distro's that go on it either.

I've never seen Arch using my swap. I think 2GB of RAM is plenty. I just keep it so I can hibernate at times I feel like. Other than that, is the scheme OK?

---

### Post by Rumor on 2008-11-14
I think that is a pretty good set up. It differs from mine in that I don't have /var on a seperate partition. If I were running a server, I would.

You might want to consider giving a bit more space to your / partition. I recently reinstalled Arch on my main computer. I gave / a lot of room, probably too much room, but it is using 7 gigs now:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb3             51815284   7088688  42115232  15% /
/dev/sdb1                38888      8851     28029  24% /boot
/dev/sdb4            254082648  49141164 192136476  21% /home

```You might want to bump yours up depending on how much software you plan to install and whether or not you're going to tinker much :-)

---

### Post by kpkeerthi on 2008-11-14
> **Rumor said:**
> I think that is a pretty good set up. It differs from mine in that I don't have /var on a seperate partition. If I were running a server, I would.

You might want to consider giving a bit more space to your / partition. I recently reinstalled Arch on my main computer. You might want to bump yours up depending on how much software you plan to install and whether or not you're going to tinker much :-)

Thanks for the feedback. I'm usually picky about the softwares I use and have a list for myself that I normally use. In my year's Arch use, / has not crossed 3.5 GB. Yeah but thanks anyways for the advice.

---

### Post by fwojciec on 2008-11-14
> **kpkeerthi said:**
> I've installed many distros in the past and as a result my current partition layout is, well, out of order. Now, I just want to keep Arch and nothing else. 

I'm going to format and restructure as below:

HDD: 100 GB, RAM: 2 GB
```

/         10 GB      as JFS
/var      2 GB       as ReiserFS
swap      2 GB     
/home  <remaining>   as JFS

```

Is the partitioning scheme OK? Is the order really important? Thanks in advance for your suggestions.

I'd do:
500MB ext2 /boot
10-12GB reiserfs /
rest jfs /home
+swap

I don't know why people insist on making only /var as reiserfs.  Separate /var results in an inflexible setup where you constantly have to worry about the amount of cached packages and such.  Reiserfs is the only filesystem that makes meaningful, noticeable difference in system performance, and the vast majority of files on / do benefit from using reiserfs (i.e. you have virtually no large files there, and a whole lot of small files).  If you just use reiserfs on /var you will only see it's benefits when you run pacman, if you use it on the whole / you will see it's benefits when you run everything.

Separate boot -- is always a good idea, IMO.

For home you can use anything, so you can use JFS if you prefer.  In my experience JFS is reliable, it is -- supposedly -- cpu/power efficient, but it is also unexceptional in every other sense -- including performance.

---

### Post by MisfitI38 on 2008-11-14
2 gig /var is pretty small..I would up that significantly.
;)

---

### Post by handy on 2008-11-14
> **kpkeerthi said:**
> I've never seen Arch using my swap. I think 2GB of RAM is plenty. I just keep it so I can hibernate at times I feel like. Other than that, is the scheme OK?

Ahh, yes, I always forget that other people use hibernation... :lolflag:

---

### Post by kpkeerthi on 2008-11-15
OK... I just quickly formatted some unused disk space to reiserfs. rsync'ed current /var to it and mounted it as /var in FSTAB. I've never seen pacman as zippy before (on ext3)

---

### Post by kpkeerthi on 2008-11-15
> **fwojciec said:**
> 
For home you can use anything, so you can use JFS if you prefer.  In my experience JFS is reliable, it is -- supposedly -- cpu/power efficient, **but it is also [COLOR="Red"]unexceptional[/COLOR] in every other sense** -- including performance.

fwojciec, Is that a typo? Do you mean nothing radical in JFS... seriously?

---

### Post by medic2000 on 2008-11-15
> **fwojciec said:**
> I'd do:
500MB ext2 /boot
10-12GB reiserfs /
rest jfs /home
+swap

I don't know why people insist on making only /var as reiserfs.  Separate /var results in an inflexible setup where you constantly have to worry about the amount of cached packages and such.  Reiserfs is the only filesystem that makes meaningful, noticeable difference in system performance, and the vast majority of files on / do benefit from using reiserfs (i.e. you have virtually no large files there, and a whole lot of small files).  If you just use reiserfs on /var you will only see it's benefits when you run pacman, if you use it on the whole / you will see it's benefits when you run everything.

Separate boot -- is always a good idea, IMO.

For home you can use anything, so you can use JFS if you prefer.  In my experience JFS is reliable, it is -- supposedly -- cpu/power efficient, but it is also unexceptional in every other sense -- including performance.

Why 500MB for boot?

---

### Post by fwojciec on 2008-11-15
> **kpkeerthi said:**
> fwojciec, Is that a typo? Do you mean nothing radical in JFS... seriously?

Reiserfs -- exceptionally fast in general use
xfs -- exceptionally slow in general use
ext3,jfs -- performance-neutral, unexceptional

Sorry if my nomenclature is confusing ;)

> **medic2000 said:**
> Why 500MB for boot?

Do you mean why so much or why so little or separate boot at all?  500MB is a pretty arbitrary number -- I used to use a 100MB /boot, but I did manage to run out of space on that partition in the past so I started using 500MB /boot partitions.

---

### Post by mips on 2008-11-15
> **fwojciec said:**
> 
xfs -- exceptionally slow in general use


******** I say ;)

---

### Post by WaeV on 2008-11-15
I plan do do the following:

100 GB NTFS Windows
Logical:
---50 MB ext2 /boot
---112 GB jfs /
---11 GB reiserFS /var
---1 GB swap

---

### Post by handy on 2008-11-15
Whenever I read about ReiserFS it just looks to have too many vulnerabilities to risk using.

Any speed increase becomes null & void after your partition becomes corrupt.

---

### Post by fwojciec on 2008-11-15
> **handy said:**
> Whenever I read about ReiserFS it just looks to have too many vulnerabilities to risk using.

Any speed increase becomes null & void after your partition becomes corrupt.

If you search hard enough you'll find horror stories about every single filesystem type.  The point is -- things always can go wrong.  This is why one should have a good backup solution implemented (it's easy with cron + rsync).  Even if my / partition dies I think I'd be able to restore its contents in about 1-2 hours.  Having said that: I've been using reiserfs for almost 2 years now and I've never had any problems with it.

---

### Post by WaeV on 2008-11-15
I agree with handy, there are many complaints about corruption with reiser, but the speed increase you get with pacman if you use it with /var seems to be intense.

---

### Post by fwojciec on 2008-11-15
> **WaeV said:**
> I agree with handy, there are many complaints about corruption with reiser, but the speed increase you get with pacman if you use it with /var seems to be intense.

I hate when people spread FUD about a piece of software, because it is highly disrespectful to those who contribute to it's development.

I urge you to do a little experiment.  Google "reiserfs + corruption" and then google "ext3 + corruption" and then google "xfs + corruption" and then google "jfs + corruption" and then explain to me why you're singling reiserfs out as an unstable filesystem?

---

### Post by kpkeerthi on 2008-11-15
> **fwojciec said:**
> Reiserfs -- exceptionally fast in general use
xfs -- exceptionally slow in general use
ext3,jfs -- performance-neutral, unexceptional

Sorry if my nomenclature is confusing ;)

Thanks for clearing that up.

---

### Post by handy on 2008-11-15
From what I have read, JFS looked to be the most reliable after ext3.  So those two are what I use.

I know they are all capable of falling in a heap given the right set of circumstances.

It is not my intention to spread FUD about ReiserFS, I read about them all & made my choice in the interest of reliability.

P.S. I'm fortunate in that I don't know what hate feels like, I also try hard to be free of chauvinism.

---

### Post by WaeV on 2008-11-16
> **fwojciec said:**
> I hate when people spread FUD about a piece of software, because it is highly disrespectful to those who contribute to it's development.

I urge you to do a little experiment. Google "reiserfs + corruption" and then google "ext3 + corruption" and then google "xfs + corruption" and then google "jfs + corruption" and then explain to me why you're singling reiserfs out as an unstable filesystem?

**Google hits:**
ReiserFS corruption - 133,000
ReiserFS - 1,660,000
ext3 corruption - 164,000
ext3 - 3,770,000
xfs corruption - 75,400
xfs - 2,190,000
jfs corruption - 35,300
jfs - 1,590,000

**Percent of arcticles pertaining to corruption:**
ReiserFS - 8.0%
ext3 - 4.3%
xfs - 3.4%
jfs - 2.2%

ReiserFS becomes corrupt twice as often as the others, according to the google hits.

---

### Post by fwojciec on 2008-11-16
@WaeV

LOL. Very clever.  But the methodology is a bit dodgy I think:

linux unstable: 2,120,000
linux: 446,000,000
"windows xp" unstable: 459,000
"windows xp": 205,000,000

Percentage of articles related to unstability:

Linux: 0.47%
Windows XP: 0.22%

Result: Linux is twice as unstable as Windows XP, according to google hits.

Anyways, this is a pointless debate -- so I'm done with it.

@kpkeerthi: Sorry for derailing your thread like this.

---

### Post by handy on 2008-11-16
***@kpkeerthi:***

With partitions starting from the center of the disk, I would think your partitioning order looks pretty good. :-)

---

