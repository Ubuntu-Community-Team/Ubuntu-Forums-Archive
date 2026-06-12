---
title: "reverting to windows"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by aykay on 2007-06-06
well, as much as I like ubuntu, there's just not enough software support...so I need to get back to windows. (I do plan on dual booting).

I initially installed ubuntu when I corrupted my windows registry, and had no repair disk available. I was curious to begin with, so I wasn't too bothered by it. I figured I'd install it, try it out, and then reinstall windows. I formatted my hdd (all my stuff was backed up, thank god) and installed ubuntu.

but now I'm having troubles getting back. I installed gparted with root permissions and all that, but it looked dangerous, so I left that alone. can someone give me a step by step of what I should do? I'd really appreciate it.

---

### Post by justin whitaker on 2007-06-06
> **aykay said:**
> well, as much as I like ubuntu, there's just not enough software support...so I need to get back to windows. (I do plan on dual booting).

I initially installed ubuntu when I corrupted my windows registry, and had no repair disk available. I was curious to begin with, so I wasn't too bothered by it. I figured I'd install it, try it out, and then reinstall windows. I formatted my hdd (all my stuff was backed up, thank god) and installed ubuntu.

but now I'm having troubles getting back. I installed gparted with root permissions and all that, but it looked dangerous, so I left that alone. can someone give me a step by step of what I should do? I'd really appreciate it.

What I would do, in your case, is back everything up again, and install XP first, then carve out an Ubuntu partition. 

You can resize your Ubuntu partition, and format a slice in NTFS via gparted...but if you just have recovery discs for your system, and not a real single XP CD, it's going to nuke your HD anyway. If you have a single disc XP install disc, you will still have to reinstall grub, or install a boot manager, because XP writes over the MBR.

I just reinstalled Ubuntu after spending a few days XP only. Couldn't stand it. Had to get back to the open country. :P

---

### Post by Happy_Man on 2007-06-06
Yeah, install Windows first. It likes thinking that it's the only OS on your system, and so it must _absolutely positively_ format the HDD before installing. Bye Ubuntu! So, go ahead, back up anything you want, install XP, and then install Ubuntu again. 

> reverting to windows

Thought i'd have to convince someone getting angry wasn't worth it, then I read he'd be dual-booting.

---

