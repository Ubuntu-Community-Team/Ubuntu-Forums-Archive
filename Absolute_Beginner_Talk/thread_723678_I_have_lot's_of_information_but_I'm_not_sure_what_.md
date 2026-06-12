---
title: "I have lot's of information but I'm not sure what to do with it."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by geemcd on 2008-03-13
Hi,

I'm trying to install any version of ubuntu on my fujitsu siemens amilo L7300 laptop. I have run into a few problems.... refer 

[http://ubuntuforums.org/showthread.php?t=720763&highlight=amilo+l7300](http://ubuntuforums.org/showthread.php?t=720763&highlight=amilo+l7300)

Now I have some detailed information on how to do it but the information assumes a lot of knowledge that I just don't have. So, can anyone decode this for me...

[http://www.init0.nl/amilol7300.php](http://www.init0.nl/amilol7300.php)

Thanks in advance,

Glenn

---

### Post by spiderbatdad on 2008-03-13
Well that guide refers to much older kernel versions. You would most likely be installing on 2.6.22-14
Have you tried using any boot parameters by pressing f6 at the install options screen and entering the parameters manually? For example: noapic nolapic  You might also try all_generic_ide

---

### Post by geemcd on 2008-03-14
Hi spiderbatdad, 

I tried booting up with those parameters and it almost worked. It got further than ever before but still no ubuntu.. 

I got a menu to select screen resolution then a whole bunch of processes started up, followed by screens of I/O and squasfs errors then it claimed to be running boot scripts and hung. There was a cursor on screen but no prompt.

So near yet so far!

Any help much appreciated.

Glenn

Edit: I tried again with a Kubuntu 6.06 live cd I had lying around, using the same boot parameters and got this message...

(4294667.296000) SMP mp table: bad signature (0x0)!
(4294667.296000) BIOS bug, MP table errors detcted!...
(4294667.296000) Disabling SMP support. (tell your hw vendor)
(4294667.977000) PCI: Failed to allocate mem resource #6:10000@f4000000 for 0000:01.0

and a cursor with no prompt.

Is PCI something to do with the graphics card?

---

### Post by geemcd on 2008-03-19
I'm not having much luck here and don't really know anyone personally who can help so for now the whole Linux thing is on the back burner. /hdb or as it's now called  D:  is going to be storage for porn, music and porn. and other such things. Thanks for trying to help folks!

Glenn

---

