---
title: "from new Ubuntu-er: RAID &amp; Mac Network"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-05
I just bought a PC today (having been a Mac man my whole life) for the express purpose of running Ubuntu & especially Amarok... without getting into any Amarok questions, I had two specific linux-ubuntu questions:


1 - I know Linux can work with RAID, the same as MAC OS X does - is there an equivalent of DISK UTILITY if I want to put two or more hard drives in a RAID structure?


2 - I need for my Mac and my new Linux machine to be able to see each other on my little home network (mainly so they can share music files) - as of now, they do not seem to be aware of each other at all... what's the easiest way to get them to see each other?

thanks!

W

---

### Post by bongobonga on 2007-09-06
1: The utility that you are looking for is "mdadm" it is used for creating raid structures. I've only ever used it to create RAID 1, but it can be used for other variants. 

2: I have set up a samba server on my linux box at home. Samba is a server for creating network drives. With this I have no problem with sharing files across windows/linux/mac.

Hope this gives you a starting point to solve your problems.

---

### Post by willfriedwald on 2007-09-06
thank you!

MDADM - that's a utility?  Can I install it using the very convenient feisty fawn add/remove programs thing?  That's very easy.  Otherwise, where can I find it?  (I hope it's not a command line terminal thing - they scare me to death!)

same with Samba - do you know where to find that?  Hopefully that's also an easy-to-use program.

will look into them both right away.

thanks muchly!

will

---

### Post by annda on 2007-09-06
hi,

not much on the RAID issue, but as to ubuntu/mac sharing you might read those 2 forum threads:
[http://ubuntuforums.org/showthread.php?t=504879](http://ubuntuforums.org/showthread.php?t=504879)
[http://ubuntuforums.org/showthread.php?t=505034](http://ubuntuforums.org/showthread.php?t=505034)

there is a lot more information out there, but being rather a linux native experimenting with macs this in all i have to offer for further reading (i believe little is better than nothing).

---

### Post by willfriedwald on 2007-09-06
thanks - I followed the trail - and came up with the same end result... (I put some of this on the other thread you referred me to, but am elaborating on it here..

on the Mac end - this is what happened (the same thing happened to someone else in the thread) : hey - I tried this and had the exact same situation - the linux system shows up in the mac network, but then when I try to connect, I get the same message: "the alias 'linux' could not be opened because the original item can not be found.'

has anyone come up with a solution for this?

for a few seconds I was hopefully - that I could actually access the linux files through the Mac without having to go through SAMBA (which I haven't even tried to do yet...)

anyhow, am curious if there's a way to do it - SAMBA looks incredibly complicated, even though I appreciate that whoever developed it came up with a musical name!

on the linux end, however, I was able to connect back to the Mac - however so far I can only reach the main drive, I can't connect to any of the other internal (or external drives) - anyhow, something is happening, I am happy to say...

will


will
__________________

---

