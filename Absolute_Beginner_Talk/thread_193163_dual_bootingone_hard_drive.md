---
title: "dual booting/one hard drive"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by r3st on 2006-06-09
I have been trying to figure out how to dual boot.  I've been using google to find an answer but all I find are instrucions on how to dual boot with 2 hard drives.  I have one 200GB hard drive.  It is partioned except for 30GB which is unallocated and I thought I was going to be able to installed ubuntu on that.  I have seen the video.google.com dual boot video so please don't link me to that.    I have tried different ways of installing it but when I restart after installing it doesnt ask me what i want to boot to.

---

### Post by aysiu on 2006-06-09
Try this:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by brentoboy on 2006-06-09
does it boot to windows, or linux?  (after not giving you a choice)

it should be as easy as runing the installer, and when it asks how you want to do hard drives, tell it to go custom, take your thirty GB and divide it into a 1 GB swap, and the rest mount as  / (root)

then, make sure the partition for / is "bootable" (one of the options in the partion editor

and when it asks you if you want grub, say yes and put it on the Master Boot Record (MBR)

works like a charm

---

### Post by r3st on 2006-06-09
It was booting to windows
I will try that 
Thank you

---

### Post by r3st on 2006-06-09
another thing
if i have 2GB's of RAM is a swap really needed?

---

### Post by aysiu on 2006-06-09
[QUOTE=r3st]another thing
if i have 2GB's of RAM is a swap really needed?[/QUOTE]
It's not needed for functioning, but the desktop install CD may force you to create a swap partition, however small.

---

### Post by brentoboy on 2006-06-09
nope

I wouldnt make a swap drive for that, it can only slow you down, the os might page stuff out of memory (to be conservative) that could just stay in memory.

guys with 64MB of ram and 512MB of swap work fine, so obviously 2 GB is enough.
mine has swap drive becuase I have a decent amount of ram, and I have no issues at all, and I use it as a "server" to run Xwindows sessions on my older PCs.  it is a busy box, and I dont need swap.

---

### Post by r3st on 2006-06-09
worked
i dont know what was going on before

---

### Post by Ben Logan on 2006-06-13
Newbie here.  I came across this thread hoping to find info on how to set up my one-hard-drive work computer as a dual bootable machine.  I discovered this link on another thread.  I'm reposting it here, in case you find it as useful as I do: 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This link will take you to the "Illustrated Dual Boot Site."  

Enjoy!

---

