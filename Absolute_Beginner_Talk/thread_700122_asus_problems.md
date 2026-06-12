---
title: "asus problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Chronotrigger_BG on 2008-02-18
Hello

Recently I Installed ubuntu 7.10 on my Desktop and was absolutely amazed with the quality of the system. Naturally, I set off to install it on every computer that I use.

But when I tried to install it on my notebook - something went horribly awry...

Here are my specs:

Asus F5Rseries
CPU - Duo T2080 @ 1.73GHz
Display 15.4" WXGA
1024 MB RAM
Graphics: ATI Radeon Xpress 1100
I have a fresh ubuntu installation, dual-boot with ubuntu being on the second partition and about 10 GB swap memory.

Here follows a list of my problems. If anyone has had similar problems, please let me know how you have solved them.

First and foremost - there is something wrong with the graphics. Everytime I boot up it takes the computer way too long to load X - a couple of times it didn't load it at all. Definitely takes more than a minute, sometimes two. That just doesn't sound right. Also, X itself is broken. Whenever I close it, I get some random characters dumped on the screen (with command-line-like graphics) for about half a second before it shuts down. And about half the time it does load some very basic stuff just doesn't work. Stuff like refreshing the contents of a resized window or not having random lines appear around the desktop.

Also, even though all of the advanced desktop effects are working fine, without slowing down the computer one bit, I can't seem to be able to run any other graphics at all. Even the most basic of games are very choppy or laggy, not running fullscreen properly or at all.

And I can't get the wireless internet to work (other notebooks are already connected to this network and I have connected to a wireless network with this computer before.

And last but most important - every time my monitor shuts off - it shuts off permanently.
No hibernate, no suspend - if you get to power management, cold reset is the only thing that can be done. Seeing as how this is a portable computer, battery conservation is of great importance...

So, please help me to make this a working, quality installation.
Everything, short of actually replacing hardware, will be considered and also I'm not afraid to use the command line.
Thanks in advance for any hints and tips, guys :)

---

### Post by Fechter on 2008-02-18
&#1056;&#1072;&#1076;&#1074;&#1072;&#1084; &#1089;&#1077;,&#1095;&#1077; &#1087;&#1086;&#1087;&#1072;&#1076;&#1072;&#1084; &#1085;&#1072; &#1073;&#1098;&#1083;&#1075;&#1072;&#1088;&#1080;&#1085; &#1074; &#1090;&#1086;&#1079;&#1080; &#1092;&#1086;&#1088;&#1091;&#1084;.
Well I see you have 1Gb of Ram, then why 10 gb swap? Your swap should be 1,5GB

About the graphics, I have also experienced problems with compiz+ any kind of video, so if you want to get things to work smoothly try to turn off the effects. By the way, did Ubuntu
fetch all the drivers?

Abouth the network, if entering with username and password, try

sudo pppoeconf

I hope have been helpful.

---

### Post by Arthur Archnix on 2008-02-18
ATI is a monster on Linux. Nvidia is much better. What you want to do is in a terminal type:
```
lspci | grep Display
```
Take that detailed output and use it to search the forums for people with the same card. I suspect you'll find many posts and many people experiencing similar problems.

---

