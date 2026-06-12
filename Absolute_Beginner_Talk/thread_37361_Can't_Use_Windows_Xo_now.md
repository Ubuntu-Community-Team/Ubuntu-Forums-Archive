---
title: "Can't Use Windows Xo now"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by daush on 2005-05-26
hello!
hey. i use the live cd to see this linux :D
but now when i start de PC windows xp sayd. failure boot device and bla bla, change de bios and other thing.
what i have too do? this pc its not mine  :|

---

### Post by fabiodsp on 2005-05-26
i'm with a similar problem. i was trying to install ubuntu whem a alert message said that was not possible install because i not have free space, so i abort the instalation, after i can't inicializate/stat my winXP, a message says something like this 'press to reboot'. so my winXP don't loads. and now, what can i do?????

---

### Post by The Na Kun on 2005-05-26
fabiodsp, 
Did you even create a partition for linux?

daush,
Did you even take the cd out of the drive?  I'm guessing you did and it's just not working, but maybe you left it in and it isn't working this time..  I'm thinking it just isn't working..

---

### Post by fabiodsp on 2005-05-27
yes, i've created \, home and swap. but the big problem is the winXP tha dont starts.

---

### Post by Stealth on 2005-05-27
Can you guys see your XP drives intact under Linux?

---

### Post by nocturn on 2005-05-27
AFAIK, the livecd does not modify the harddisk (unless you mount something yourself).

---

### Post by David Kaisemann on 2005-05-27
[QUOTE=fabiodsp]yes, i've created \, home and swap. but the big problem is the winXP tha dont starts.[/QUOTE]

Use* Norton Disk Editor* or *PartitionMagic *(or* fdisk*) and check that your Windows XP partition are *active partition *(boot, etc.) But this programs must be on bootable CD and start from it (like LiveCD).

---

### Post by daush on 2005-05-31
ok. 
i fix the problem. when used ubunto livecd they change e BOOT CFG of windows. then waht i have to do is:
insert the windows xp cd. use console repair.
then i digit:  /fixboot
/replace bootcfg

and then!

;)

---

### Post by valchau on 2007-07-11
What you describe (can no longer boot WinXP after installing ubuntu Feisty Fawn on dual boot) is my problem as well. I read this thread's postings and I will do my best to fix my PC later when I get home. Using ubuntu I can do alot of what I used to do on Windows, so I don't really need to boot windows often now; however my Thunderbird mail folders on the WinXP drive can't be used by my Thunderbird on  ubuntu even though I copied them over. Also I need some guildance on how to install the Minolta print drivers I downloaded...

Thanks!

---

