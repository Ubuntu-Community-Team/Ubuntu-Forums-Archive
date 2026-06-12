---
title: "Help! Root file system broken? Can't start-up."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by NealeC on 2006-08-26
Whenever I boot up my machine, it will load normally until it comes to the "checking root file system" part, in which it will show this error:
[B]
/dev/hda1 has been mounted 30 times without being checked, check forced. [/B]

Then it will display, after the check: 

**[Numbers] Buffer I/O error on device hda1, logical block [more numbers]**

That will display several, several, several times with different sets of numbers each time.  It will continue to ceank out new displays, until it gives me a root@Neale:~# line. 

Hopefully someone can make sense of this. [-o<

---

### Post by Paul133 on 2006-08-26
So you turn on the computer, it goes into Grub, u highlight Ubuntu and press enter ans then it starts loading and fails here. What is the breakdown of your partitioning? You have a swap partition and a partition mounted at swap? Are you dual booting or anything? Was this working before?

---

### Post by NealeC on 2006-08-26
There's no highlighting involved.  Grub automatically loads Ubuntu, I suppose.  I'm not dual booting, Ubuntu has the only partition on my machine, but I'm not exactly saavy with the composition of it.  It was working perfectly before, so it seemingly just "crapped out" on me yesterday morning.  :) 

I've got no idea whether or not I've got a "swap" partition, only that Ubuntu is the only OS installed on my machine.

---

### Post by v1ct0r on 2006-08-26
Sounds bad...
[http://kubuntuforums.net/forums/index.php?topic=8155](http://kubuntuforums.net/forums/index.php?topic=8155)

---

### Post by NealeC on 2006-08-26
Well, those cats are having problems with their desktop hardware.  I would think that a laptop wouldn't tend to have cable management issues. 

Are there any commands I could use from the terminal? At this point, it's the only thing I can use.

---

