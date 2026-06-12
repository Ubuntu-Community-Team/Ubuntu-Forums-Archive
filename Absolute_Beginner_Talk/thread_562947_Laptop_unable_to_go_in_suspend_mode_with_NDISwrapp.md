---
title: "Laptop unable to go in suspend mode with NDISwrapper &amp; dongle"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-29
I use Feisty 7.04 on my laptop, and the suspend mode has always worked perfectly. This week I have installed NDISwrapper to work with my Netgear WG111v2 wireless dongle. It works wonderfully, the online connection is great. The only problem is that if I go off-line and try to put the computer in suspend mode, then the computer freezes and I have to power it off and reboot. 

------------------------------

What I described just above is the essential problem, and I have been unable to solve it. Further detail about what I have tried (without success), follows below:

I have installed a utility from Synaptic called "netapplet", which functions very well, and I use it for  going on- and off-line while the dongle is plugged in. 

My problem now is, that once I go online, then I can't remove the dongle without having the computer freeze. If I take the dongle out when the computer is online, then the computer freezes. And if I go offline using netapplet and THEN take out the dongle, the computer still freezes. Once it freezes, then the only thing I can do is power down the computer and reboot.

So, I thought that's fine I'll just leave the dongle in all the time once I've gone online. I don't have any problem leaving it in. That would be an alright solution.

BUT-- I do need to be able to put in suspend mode. My computer is old, and quite slow to boot up. If due to the dongle, the only way I can leave the computer for a half hour is to completely shut it down, then that is extremely inconvenient for me. I can't have any work I'm in the middle of remain active and just suspend the computer as I always do.

So I tried to "unload" NDISwrapper prior to putting the computer in suspend. Someone instructed me do the following:

"Try running sudo modprobe -r ndiswrapper, take the dongle out, and suspend. Then resume, open a terminal and type sudo modprobe ndiswrapper, wait a few seconds and try connecting with netapplet." 

I just tried it. I was online with the dongle. I opened a terminal window, typed in the command sudo modprobe -r ndiswrapper, then it asked me for my password, and as soon as I typed it in and hit enter, the computer froze. I had to power the computer down.

I also tried it first going off-line and THEN doing the "sudo modprobe -r..." command, but the computer froze up just the same and had to be powered down.

Any idea as to how I could solve this, so I would be able to use suspend mode with the dongle?   (--Either with the dongle still in, or by removing it-- either would be fine with me.)

---

### Post by swarup on 2007-09-29
Anyone have any thoughts on the above?

---

### Post by swarup on 2007-10-14
Sorry to bump this, but I am still having the problem described above. Does anyone have an idea how to solve it? Thanks.

---

