---
title: "Ubuntu hangs from time to time"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by thoddler on 2007-11-07
Hi!

I've been wondering about installing Linux for some time, and last week I decided to try Ubuntu in a dual boot with XP.
After a while I got most of my hardware to work, except of my Atheros wlan-card. I tried the regular Ubuntu (gutsy) and Kubuntu, but couldn't get it to work. Even with the help from similar threads here, and using the ndiswrapper and so on.
But yesterday I installed Linux Mint Daryna (beta, with xfce desktop environment), and finally, it worked :)

The thing is, I want to make the final transition from windows, but one problem bothers me.
From time to time, when using the OS, (what I'm doing seems irrelevant - I can't find a pattern) everything hangs for 20 seconds. Quite accurately, I've been counting ;)
When this occurs, I can move the mouse and change between open windows, but whatever I click doesn't react until after this 20 second period. But one thing I CAN do, is resume watcing a movie (I use VLC) if I've paused it earlier.
This has been happening with all three distros based on gutsy, Quite annoying.

Some info about my hardware:
Acer travelmate 2480 with intel 945GML chipset
Intel Celeron M 1,6 Ghz
1GB RAM
19" external lcd display (if that matters)

I am not skilled enough to figure this out by myself, so I hope that someone here can help me :)


-Thomas

---

### Post by dcstar on 2007-11-07
> **thoddler said:**
> 
..........
The thing is, I want to make the final transition from windows, but one problem bothers me.
From time to time, when using the OS, (what I'm doing seems irrelevant - I can't find a pattern) everything hangs for 20 seconds. Quite accurately, I've been counting ;)
.........

If you are still using the "Basic" 386 kernel, I would try installing a 686 version (the lowlatency or -rt versions).

I would also disable IPv6 as there could be timeouts occurring if Ubuntu thinks it is available in your environment.

---

### Post by TeaSwigger on 2007-11-07
This doesn't occur in windows? If it did I'd wonder about the hard drive, but if not I defer to anyone else on the matter. And you're welcome here, don't misunderstand, but if Mint has its own forums they may be more able to tackle the specifics where there may be differences.

---

### Post by thoddler on 2007-11-07
> **dcstar said:**
> If you are still using the "Basic" 386 kernel, I would try installing a 686 version (the lowlatency or -rt versions).

I would also disable IPv6 as there could be timeouts occurring if Ubuntu thinks it is available in your environment.

I guess I am using the 386 kernel. What's the difference between this and the 686-version?

I searched a little about that possible IPv6.problem and found this in one forum thread: 
"One thing you can try is, with IPv6 enabled, to launch a terminal, and
type 'host [www.google.com](www.google.com)'. If the command succeeds quickly, listing
Google's IPs, then you're not having general network connectivity
trouble(...)"
I did this, and it seems everything works as it should. So I guess thats not what causing it.


> **TeaSwigger said:**
> This doesn't occur in windows? If it did I'd wonder about the hard drive, but if not I defer to anyone else on the matter. And you're welcome here, don't misunderstand, but if Mint has its own forums they may be more able to tackle the specifics where there may be differences.

No, I don't have this problem in Windows.
I'll try asking in the Mint forum as well, but as I said, the same thing also happened with Ubuntu and Kubuntu. And I had already registered here, that's why I asked you :)


Thanks to both of you for trying to help :)

---

