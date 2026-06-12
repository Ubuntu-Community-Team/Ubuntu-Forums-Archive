---
title: "[SOLVED] Moving from hotCD to Ubuntu OS on hard Drive"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by comradelurcher on 2008-03-07
Advice!
What I would like to do is move from HotCD to hard drive Ubuntu! I have 2(two) hard drives on my pc, one with XP and all its rubbish, _another_ that I have been using for programmes, savesetc, which has been 'partitioned' by shop techie into three. On Ubuntu installer.it 'recommends'? to do its own partitioning of xp drive!,and I take it ,put Ubuntu on xpdrive, 
1. Do I Trust it , not to 'disturb' windows XP, which at the moment I am a little hesitant to let go.
2. could I therefore put Ubuntu on second drive? but how? again without messing with stuff thats already there!
For all this please remember that I am a complete newbie to all this stuff, growed up with Windows and therefore used all their rubbish, but am now rather disillusioned, and need a goal to give me pleasure when sitting at the machine!  Ta!

---

### Post by startherepodcast on 2008-03-07
Ok, so here is what you want to do:

In the Ubuntu installer, select something like "I will partition the drive myself", its the bottom option.
Then you select where you want to install (As I understand your second HD). It's a bit more difficult like this because you have to select what you want to format it as. Once you found your harddrive you want to install on, simply select ext3  and mountpoint /
Hope this helped

Leon

---

### Post by Paqman on 2008-03-07
You won't be able to put Ubuntu onto your second drive easily. Drives have a maximum of four primary paritions, and you alreayd have three. Ubuntu normally needs at least two ( a "root" partition containing the actual system, and tiny "swap" partition that works like a pagefile in Windows) It's possible to breka the four-partitions rule using something called an extended partition if you want to look into that.

Otherwise i'd say let Ubuntu resize your Windows disk and partition it. You'll need to defrag and _back up_ your Win install beforehand though. Ubuntu will need about 10GB of free space, so make sure you've got that much free space (plus a bit extra for Windows)

Psychocats has lots of information about [disk partitioning for Ubuntu](http://www.psychocats.net/ubuntu/partitioning), or you can just let the installer do it automatically.

---

### Post by comradelurcher on 2008-03-07
AH Thought I was clever, didn't need what was on my 2nd drive and Ubuntu gave me the option to install on said drive. So I did !All went well untill  going back to WINDOWS, Could not see 2nd drive under My Computer???  And then tried to boot back into Unbuntu, and it came up , but in only top half of screen BUT 4 copies so therefore could not see anything and again , could not get into Ubuntu, have you got any other ideas!!!What have I done!!!Hoping you can help..

---

