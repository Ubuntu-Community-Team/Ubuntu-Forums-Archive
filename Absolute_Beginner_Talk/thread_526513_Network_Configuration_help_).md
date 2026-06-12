---
title: "Network Configuration help :)"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by bloodysham8@msn.com on 2007-08-15
hey there

I have recently installed Ubuntu on a partitioned hard disk with XP for use while i am learning to walk on Ubuntu. 

I'm running the ubuntu 7.04. 

So, my problem. 

When i load into ubuntu, my default settings can see my flat's shared linksys connection, and I can also see my next door neigbors wireless connection.

Now, does this mean that my card is able to detect wireless connections in close proximity? In effect my card is working under ubuntu? 

Now, i have the ever popular Belkin wireless G plus mimo USB. 

I followed this guide. [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

To use the correct rt73 driver. 

The problem i am left with is that i can* see* my wireless connection but cannot input my details to actually connect to it. 

When i click on the interent icon on the desktop toolbar, and i edit the properties of WLAN0 then it no longers sees the linksys connection or my next door neighbors. 


I would really love some help to resolve this and get cracking. But, i am also a total newbie and am still quite unsure about all the terminology and terminal commands.

---

### Post by moore.bryan on 2007-08-15
[i]let's start at the beginning: what are the outputs of ```
iwconfig
ifconfig
lspci
```
?[/i]

---

