---
title: "Gutsy on MacBook v3.1 (SantaRosa) crashes!"
date: 2008-02-13
forum: Apple Intel Users
---

### Post by bozzochet on 2008-02-13
Hello to all!
I look on the forum if someone else has the same problem but i didn't find nothing.
I have Kubuntu 7.10 Gutsy on a MacBook 3.1 (SantaRosa) 2,2Ghz with 4GB of RAM.
Always (I use the computer for 10 hours every day and this appens 1-2 times for day) my Kubuntu crashes and I cannot make anything: no CTRL+ALT+DEL, no CTRL+ALT+BACKSPACE, even the mouse arrow is not responding...
Somebody has the same problem?
Somebody can help me?
Somebody knows where the problem can be?
Thanks

P.S. Sorry for my poor English...

---

### Post by mkgkg on 2008-02-13
eih.i have the same mac but with only 1 gb of memory :(...ehehe..i have no problem of crashing during all the day..never...what kind of kernel u have? did u follow the guide of [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) or u did a kernel selfmade? i'm using gnome , not kde but i think this is not the problem.

---

### Post by mkgkg on 2008-02-13
ah...can u tell me if ur remote control it's ok or not??my  doesn't work..i don't know how do.

---

### Post by bozzochet on 2008-02-13
I use the kernel (2.6.22-14.47.0cwi2) from launchpad (as following the wiki linked above). I have the same problem using the "server" (for seeing all the 4GB) one or the "generic" one. However I had the same problem also with the kernels from the official repo!

P.S. I'm not able to use the Apple Control but i didn't spend too time on it

---

### Post by mkgkg on 2008-02-13
really strange..but every time  before your os crashes u re doing something in particular??using always this application o something else??how much swap do u have?

---

### Post by bozzochet on 2008-02-13
No! It appens with no special application or feature, and almost never during an intense use of PC; just normal use.
The only 2 "constant" that I see every time are:
- the use of wireless (never crashed with the LAN connection, but I used LAN for 1% of time with respect of wireless and so can be only a coincidence)
- the "coolness" of PC (It appens when I have started up the PC from maximum 30 minutes, but usually after 5-10, and only 1 times appened after 2 hours).

I have few swap (256MB) really! I had never thought to this possibility, the problem is that having swap for the same (or even the double) amount of RAM for me means "losting" a good part of hard disk (consider that I have 120GB with 3 partitions+swap, 1 hfplus for MacOsX, 1 ext3 for Kubuntu and 1 fat32 for data with a vitualized Windows installed by VMWare, so for me the space is important!).
However my swap space is always clean and the RAM used is 50-60% at maximum.

---

### Post by mkgkg on 2008-02-13
hmm..the swap should be the double of ur memory, but u have a lot of ram so u can use ur os without swap.  u re using ndiwrapper with Knetwork manager?

---

### Post by cyberdork33 on 2008-02-13
Many people use no swap at all, that is not the issue.

---

### Post by bozzochet on 2008-02-13
Yes I use ndiswrapper cause I had some problem with madwifi...
The idea that the problem should be in wireless in only a "sensation", there's no evidence...

---

### Post by bozzochet on 2008-02-28
I confirm. the problem is on Wireless. Now I'm using bittorrent (ktorrent) downloading using very large amount of bandwitch and very very often by MacBook crashes (as said above). Using the LAN no crash occurs...
I tought to try madwifi instead of ndiswrapper, altought at the beginning of my installation I had some problems with it, and now I see on the Wiki that the **only** way for Santa Rosa version is ndiswrapper cause the too new wlna card...
Any idea?!

---

### Post by cyberdork33 on 2008-02-28
> **bozzochet said:**
> I confirm. the problem is on Wireless. Now I'm using bittorrent (ktorrent) downloading using very large amount of bandwitch and very very often by MacBook crashes (as said above). Using the LAN no crash occurs...
I tought to try madwifi instead of ndiswrapper, altought at the beginning of my installation I had some problems with it, and now I see on the Wiki that the **only** way for Santa Rosa version is ndiswrapper cause the too new wlna card...
Any idea?!

Yes, that is right. Madwifi is only for atheros Wi-Fi cards, you have a Broadcom card. Unfortunately, ndiswrapper is known to give people issues itself. There is no other solution for bcm4328 cards like yours (yet).

---

