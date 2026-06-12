---
title: "Error 2 loading GRUB"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by nitemann on 2008-01-07
This is a clean HD, no other Os than UB 7.10, at a loss.. If I boot from CD I ran EFSCK to check HD,  even under GUI I checked to see if it and had and  repair any errors.. Still locks up..  I left the install running  and went to bed after I saw 30 % plus still churning away.. I had posted earlier how I killed this OS when  the box lost power due to my two left feet and kick the power cord. Now.... I am about burned out..
If I boot on CD the HD shows the drive partioned as:

/dev/sda1 ext3 size 3.81 gigs - Boot - Unmounted
/dev/sda2 extended  235 Mib - Busy
/dev/sda5 linux-swap 235 MIb - Active

The extedned and swap have Lock Icons

I check thru Terminal window and it states sda1 is mounted on
/media/disk

if this a simple error it is due to my lack of UNIX/LINX basics on my part..

any help to resolve is greatl appreciated.

---

### Post by gn2 on 2008-01-07
Looks like a rather small hard drive, what's the rest of the system spec, CPU, RAM?

---

### Post by nitemann on 2008-01-07
Hi Gnu,

Tolet you know the 1st install worked and the machine ran fine..
it lost power and from then on, that became the problem.

its a PII 333 Celeron  clocked uo to 416 mgz , running 192 megs of ram and 8 meg AGP card... It ran great, not the fancy capabilites ub2 is known for, but it was destion to go to my barn as an MP# juke bok and web browers and what not.

---

### Post by gn2 on 2008-01-08
If you're attempting to run 7.10 on it you're asking too much.
The 7.10 Live CD installer requires a minimum of a P3 CPU and 384mb RAM according to the release notes and I think that's actually not enough based on my own experiences.

With your system I would suggest trying Zenwalk instead.

[www.zenwalk.org](www.zenwalk.org)

---

