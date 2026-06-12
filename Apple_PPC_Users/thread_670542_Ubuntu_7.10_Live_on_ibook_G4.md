---
title: "Ubuntu 7.10 Live on ibook G4"
date: 2008-01-17
forum: Apple PPC Users
---

### Post by Dr.Greenmac on 2008-01-17
Hi dudes.
I have this ibook G4 with tiger OS X.
I wanted to use the live ubuntu 7.10 that i have just downloaded from the comunity port.
But when I boot with it, and tha black screen tells me to type " Live" or Live video=offonly" both comands take me to a white screen that say " display found" and then, it takes me to a black screen that goes nowhere, and stays like that for ever! lol.
Also just presing enter happens the same. so sad! lol
What am I doing wrong?
Should I use the other commands the the help menu tells me when i press TAB??

Please help me, I really want to use Ubuntu on my MAC, cause im an ubuntu user in PC, but I sold my pc, so i want to use ubuntu on my ibook.

Thanks a lot dudes!

---

### Post by VERiON on 2008-01-17
Maybe you can install using [alternate install CD]("http://cdimage.ubuntu.com/ports/releases/gutsy/release/ubuntu-7.10-alternate-powerpc.iso") -> this is the way I've installed my xubuntu 7.10 without any problems on iBook G4 1,33.

This is basicaly the same installer on desktop CD but in text mode.

---

### Post by Dr.Greenmac on 2008-01-17
thanks pal!

---

### Post by Dr.Greenmac on 2008-01-18
Hey, ok I have just downloaded the alternate install cd.
My quiestions are:
Am I going to be able to partition the HD from the alternate CD so that I got two partitions, one for mac and one for linux??
Or do I have to do the partitioning before I use the alternate cd??
Which program should I use and how, I really dont want to screw up my OS X until I trie the ubuntu on my mac firs.

thanks for the answers.

Bye

---

### Post by tjniels on 2008-03-18
You've probably solved your problem by now, but in case it helps, I've got a pointer - 

When you get the boot prompt, instead of typing "live" or anything like that, type 

[INDENT]code:

live-nosplash-powerpc <enter>
[/INDENT]

That got my iBook G4/800 to boot with no problems, I had to tweak the wireless drivers to get AirPort to work, but I haven't found any other problems.  Some say it won't wake from sleep, I didn't test that.  From the live CD, there's an icon that lets you install, but I'm not willing to sacrifice OS X on that machine.

Hope that helps!

---

