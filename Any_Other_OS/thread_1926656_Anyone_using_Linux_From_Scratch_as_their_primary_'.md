---
title: "Anyone using Linux From Scratch as their primary 'distro'?"
date: 2012-02-16
forum: Any Other OS
---

### Post by samalex on 2012-02-16
Hi Everyone,

I've started going through Linux From Scratch, and it's actually not as difficult as I expected.  I hope to have a working system in a week or so (just have an hour two every few days to work on it) then I hope to start tackling Beyond LFS to add more functionality to the system.

I always thought of LFS and BLFS as more of an experiment to learn Linux, but the more I get into it the more I'm really wondering if I shouldn't just scrap the distro and build my own system from ground up.  Granted updates will need to be done manually, but keeping my head in the clouds will help in identifying which packages need to be updated due to security reasons and such since I'll know EXACTLY what's on my system.

Has anyone done this???  Just curious --

Thanks,
Sam

---

### Post by Andrew_P on 2012-02-16
I was looking at Linux from Scratch last night and reading some comments about it.  Even though the project is ongoing, from what I've been able to gather it's a bit behind the technology curve and may not support the latest hardware.  Possible difficulty recognizing SATA hard drives was a specific point I saw mentioned.  If you have 5-10 year old hardware, you should be able to make a go of it.  It looks like it would be a great learning experience, if nothing else.  If you're interested in a Linux distribution to do something specific, take a look at [http://www.distrowatch.com](http://www.distrowatch.com).  It lists over 300 Linux distributions on the DistroWatch Page Hit Ranking page, most of which I'd never encountered or even heard about, and some are extremely specific in their purpose, such as cracking Microsoft passwords.

---

### Post by samalex on 2012-02-17
> **Andrew_P said:**
> I was looking at Linux from Scratch last night and reading some comments about it.  Even though the project is ongoing, from what I've been able to gather it's a bit behind the technology curve and may not support the latest hardware.  Possible difficulty recognizing SATA hard drives was a specific point I saw mentioned.  If you have 5-10 year old hardware, you should be able to make a go of it.  It looks like it would be a great learning experience, if nothing else.  If you're interested in a Linux distribution to do something specific, take a look at [http://www.distrowatch.com](http://www.distrowatch.com).  It lists over 300 Linux distributions on the DistroWatch Page Hit Ranking page, most of which I'd never encountered or even heard about, and some are extremely specific in their purpose, such as cracking Microsoft passwords.

Actually LFS 7.0 is using rather up to date packages like kernel version 3.1 which is barely a month old.  And for hardware support given the kernel is newer it should support most newer systems and standard hardware, including SATA.

For me I've used someone else's distro for a better part of 15 years now, so why not try to roll my own.  I'm not sure if it's feasible to run LFS as a primary system, but if it is possible I'd sure be game to give it a shot, hence my post.  But even if not, installing LFS should give me a better understanding of how Linux works under the hood.  Modern distros are turnkey anymore with little if any tweaking needed to get going.  And it seems debates between which Distro is best anymore are more focused on the Windows Manager which can be changed on any distro.

Anyway, just some thoughts on it --
Sam

---

### Post by Neezer on 2012-03-14
> **samalex said:**
> Actually LFS 7.0 is using rather up to date packages like kernel version 3.1 which is barely a month old.  And for hardware support given the kernel is newer it should support most newer systems and standard hardware, including SATA.

For me I've used someone else's distro for a better part of 15 years now, so why not try to roll my own.  I'm not sure if it's feasible to run LFS as a primary system, but if it is possible I'd sure be game to give it a shot, hence my post.  But even if not, installing LFS should give me a better understanding of how Linux works under the hood.  Modern distros are turnkey anymore with little if any tweaking needed to get going.  And it seems debates between which Distro is best anymore are more focused on the Windows Manager which can be changed on any distro.

Anyway, just some thoughts on it --
Sam


What distro are you using as the host system? I started looking into this as well, and thought it would be a great learning opportunity. I started running into issues though, and now I'm really busy at work...I will complete the build though.

So as I asked before what distro are you using that satisfies all the host system requirements? I tried 10.04 with no modifications to packages. I'm not sure if that is good though.

---

### Post by sadsack2 on 2012-12-22
YES!!! Have done so for ~8 years. LFS by itself is impossible without extensions via BLFS unless you are very strange and only need midnight commander and vi.
I'm not sure I want to meet this person. But in nicer times if you just built X and minimal GTK2 support setup you were likely to  be happier than the many people I see cursing some jackbooted sysadmin's idea of the proper setup.


sadsack2

---

