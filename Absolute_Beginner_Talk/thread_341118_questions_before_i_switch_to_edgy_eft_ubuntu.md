---
title: "questions before i switch to edgy eft ubuntu"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by atlfalcons866 on 2007-01-18
HI
I am trying to abandon the ms windows for good. I just have a few questions!

1.Do i have to register ubuntu to use like windows

2. is there a way to play windows games?

3.is rig fast enough to run ubuntu smoothly?

2.8Ghz pentium 4 533Mhz front side bus northwood core
512 mb 
120GB HARDDISK

4. Will i be able to resize the windows partition?

---

### Post by amo-ej1 on 2007-01-18
Hi, when you're still in a migration fase you might wish to setup your system as dual boot first in order to have a more gently switchover.

You won't need to register ubuntu, it's completely free and you pc is fast enough for sure.

Well about games, games is something that is still a bit behind in Linux/Ubuntu, however many commercial games are supported in some way but it can take some time to get them starting but there's a lot of support here, check the games forum

---

### Post by darrenm on 2007-01-18
1.Do i have to register ubuntu to use like windows

nope.

2. is there a way to play windows games?

not really. Just think no then anything you can get to work through wine will be a bonus.

3.is rig fast enough to run ubuntu smoothly?

2.8Ghz pentium 4 533Mhz front side bus northwood core
512 mb 
120GB HARDDISK

Sure is!

4. Will i be able to resize the windows partition?

Yes. Use the LiveCD installer.

Good luck! :)

---

### Post by atlfalcons866 on 2007-01-18
i only have alt installer:???:  is there a way to do it on the alternate because for somereason my cd rom drive stalls on the live cd:confused:

---

### Post by atlfalcons866 on 2007-01-18
> **amo-ej1 said:**
>  You won't need to register ubuntu, it's completely free and you pc is fast enough for sure.



that is what i love about open source products!

---

### Post by j19sch on 2007-01-18
Window games (some/most/depends) can be played with Wine, Cedega or VMWare with a Windows image. Other people can tell you more, I haven't used any of these. Dual-booting is fine as well.
And depending on what games you like, there are some great native Linux games as well. (sorry, had to mention that)

Your rig will be fine. I ran Ubuntu edgy (with gnome) on an Athlon 1800 with 256Mb RAM without a problem, running about as fast as WinXP did (never bothered to actually time it).

About resizing your windows partition: if you run into any problems, search the forum. There are some tricks to make it resizable. Worst case scenario would be backing up the data and reinstalling Windows before installing Ubuntu.

Joep

---

### Post by atlfalcons866 on 2007-01-18
this is what i am going to do with windows xp

shrink it down to 10GB cuz i only have 9GB used
allocate the rest of my hard drive to linux which is around 110gb

---

### Post by j19sch on 2007-01-18
> **atlfalcons866 said:**
> this is what i am going to do with windows xp

shrink it down to 10GB cuz i only have 9GB used
allocate the rest of my hard drive to linux which is around 110gb

You realise Win XP needs some empty space on its partition to run properly? And what if you want to install something new on Windows, install an update that needs a lot of spce, etc.? Maybe make it 15GB or something, since 105GB is more than enough for Linux:
1 GB of swap
25 GB for / (root) and that's plenty as well
which leaves 79 GB for lots and lots of data on /home.
You might want to have a Fat32 partition to share data between linux and windows, as well, btw.

Joep

---

### Post by atlfalcons866 on 2007-01-18
i have an external hard disk that 40GB Wont that work if its formated fat32

---

### Post by j19sch on 2007-01-18
> **atlfalcons866 said:**
> i have an external hard disk that 40GB Wont that work if its formated fat32
That would work. You will need to configure it so that you can mount it in Linux, but that shouldn't be a problem.

---

### Post by jvc26 on 2007-01-18
You could even format it ext3 as there is an app (somewhere on the forums, apologies but cant find the link at the moment) to a method to read ext3 in windows, and the read-write drivers for ntfs in linux. FAT32 although easy to use has the disadvantage of becoming fragmented very quickly. Good luck :) Its all free which is whats so awesome about open source things.
Il

---

### Post by j19sch on 2007-01-18
About those NTFS Linux drivers: I've heard they're still in beta.
So using them is not totally risk free. Your decission, of course.

---

