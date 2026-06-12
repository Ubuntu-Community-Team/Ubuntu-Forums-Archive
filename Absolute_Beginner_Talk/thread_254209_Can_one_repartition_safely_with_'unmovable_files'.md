---
title: "Can one repartition safely with 'unmovable files'?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by latecomer on 2006-09-09
Hi

I'd like to install Ubuntu on my laptop (HP Pavilion dv4000, Pentium M 1.73GHz, 512 MB RAM, 80 GB HD, WinXP Home SP2).
I want to do it as a dual-boot, I've read up on repartitioning my HD, going do it with GPartEd running from CD.
But one thing still worries me and before I start I was hoping if someone could offer advice. I've already defragmented my drive a few times, but what bugs me are some 'unmovable files' in my free space (see the green band to the right in screenshot.) When I resize my Windows partition will GPartEd be able to move these files or is this just going to mess up XP?
Thanking you kindly for any help
(apologies if this is not quite the right forum for my question, i'm a bit of a noob, you see :biggrin: )

---

### Post by aysiu on 2006-09-09
It won't mess up XP, but GParted probably won't let you resize beyond the right-most file, so you wouldn't have terribly a lot of room. I'm not sure how to handle that.

---

### Post by kidders on 2006-09-09
I'm convinced MS does this on purpose lol!

On thing you might want to try (assuming you haven't already) is delete your pagefiles and reboot in "safe" mode. Then close absolutely every process you can live without and try the defragmentation again. As another option, perhaps a defragmenter not written by Microsoft might force this stuff to one side for you?

---

### Post by nickpaton on 2006-09-09
Hi latecomer & Welcome to the Forums!

I would not suggest paritioning over the immovable files, since could well break your Windows Distro.

What I suggest you do is to get hold of a defrag program which will properly degrag Windows, rather than using MS's one.

I'm not meaning to advertise any particular commercial company, and leave it to moderators to amend this etc, but there is an evaluation copy of Raxco Perfect Disc, which defrags very well indeed, and should shift the 'immoveable files'.

[http://www.raxco.com/products/perfectdisk2k/]("http://www.raxco.com/products/perfectdisk2k/")

From then on you should be able to continue with partitioning and Ubuntu installation.

---

### Post by thom314 on 2006-09-09
Those unmovable green bands are Windows' swap space spread across your hard drive. Somewhere, try looking under My Computer, you can find a dialog where you can disable the swap space or set it to zero. This is safe to do at least temporarily. You might want to defragment again if these unmovable bands were impacting that. Then repartition. Then in Windows go back and re-establish its' swap space.

I would give you more details of where to look except I am on my Linux side of my dual boot laptop. I have done this myself to my version of windows so it is safe to do.

Good luck.

---

### Post by latecomer on 2006-09-09
:D thank you all for your speedy replies and especially thom314; it was indeed xp's pagefile. I disabled it, defragged again and that was that sorted. Resized my xp partition with GParted and then fired her up again and everything's working fine. Good stuff :)

---

