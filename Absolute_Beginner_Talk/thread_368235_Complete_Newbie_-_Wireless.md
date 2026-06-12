---
title: "Complete Newbie - Wireless"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by blackbird2150 on 2007-02-23
Hello everyone,
I made the switch to ubuntu about 4 hours ago.  Everything works great and i love it.
However i have one problem.  It seems to be quite common. I also just have a quick question as well.
And if i am posting in the wrong section, please forgive me, I just didnt really know where to post, seeing as how i have no prior experience with Ubuntu.
I'll start with my quick question.
I am using an Acer Laptop, and it has a touchpad mouse.  In this OS its INCREDIBLY senstive.
like i brush it accidently, and things get clicked, highlighted and deleted, etc.  Essentially is there a way lower the sensitivity?
 
Now my main issue is with my wireless card.
Like i said i have an Acer Laptop.
The exact readout of from an lspci of my wireless card is 
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I have tried the forums that walk you through it. such as:
[http://www.ubuntuforums.org/showthread.php?t=190177](http://www.ubuntuforums.org/showthread.php?t=190177)

It still doesn't work.  To elaborate a little... after running through that guide above, when i go system>admin>network  my wireless isn't there anymore, all it say it says is wired and modem.
(when i first installed ubuntu there was a wireless section, it just didn't work).

I don't know where to begin solving this problem...
any help would be greatly appreciated.
Thanks in Advance,
Stephen.

---

### Post by Henry Rayker on 2007-02-23
This will write over your /etc/X11/xorg.conf file, so I'd do a ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` just to be safe...

For my touchpad, I do a ```
sudo dpkg-reconfigure xserver-xorg
```

This will ask you a LOT of questions (concerning video card, drivers, keyboard, but also, it'll ask about the mouse protocol. I just select ExplorerPS/2 and that fixes the sensitivity...

---

