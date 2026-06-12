---
title: "Xubuntu takes a long time to start"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by tojulius on 2008-04-09
I recently formatted my Acer Aspire 1801wsmi with ATI Radeon x600 and installed Xubuntu 7.10 Gutsy from scratch.

I noted that when I turned on the laptop I immediately got a black screen and it takes up to 5 minutes to get the graphic interface to start.

I tried ctrl+alt+f1 and the log in screen immediately appeared

I noted a message saying kinit no resume image doing normal boot

I followed this advice [https://bugs.launchpad.net/ubuntu/+bug/103148/comments/50](https://bugs.launchpad.net/ubuntu/+bug/103148/comments/50)

Now I don't get the kinit message but I am not able to log in through the graphic interface unless I press ctrl+alt+f1 which triggers normal boot

Any suggestion?

Thanks

Julius

---

### Post by Crafty Kisses on 2008-04-09
Weird, can you post some of your system specs?
Also if you're not getting a GUI you might want to do the following:
```
startx
```
See what happens when you do that.

---

### Post by tojulius on 2008-04-09
There is no need to run startx as when I enter ctrl+alt+f1 the booting process starts normally and I can see the GUI screen. Otherwise the screen is black and I can tell by the sound that the CPU is heavily used it actually looks like it is hibernated.

Specs:
Xubuntu 7.10 (only OS no partitions no dual boot)
Acer Aspire 1801 wsmi_2.93
ATI Mobility Radeon X600
PCI Express/64MB VRAM
Intel Pentium 4 525 processor
512MB DDR

---

### Post by tojulius on 2008-04-10
The screen I get at Startup:

Starting Up
[ 16.071342] 00:08: SMCF01 not responding at SIR 0x3F8, FIR 0x7F8; auto configuring
[ 16.073915] 00:08: responds at SIR 0x2t8, FIR 0x240
Loading please wait

And then I got the black screen

Anyone?

---

### Post by jiangdanye on 2008-04-13
Hi Tojulius, I've the same problem. An annoying boot time of over 3 min. With Xubuntu 7.10.On a IBM T30. Also uses a Radeon soundcard (Radeon 7500),

I found this: [http://ubuntuforums.org/showthread.php?t=663638](http://ubuntuforums.org/showthread.php?t=663638)

Have you tried that?

Have you solved your issue?

I wish you good, luck. I hope I will be able to solve this for myself.

Regards, D

---

### Post by tojulius on 2008-04-13
Worked like charm, completely spot on.

Thanks jiangdanye

Julius

---

