---
title: "Alcatel USB Speedtouch 330 Firmware"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by JanCoonen on 2006-10-21
Hey Everybody,

I'm trying to get my alcatel USB Speedtouch 330 (green one) up and running in Ubuntu. In this howto ([http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)) I've read that I need to change the firmware. What does this mean? Does such an action change somehing "in the modem" itself? Rewrite the modem EPROM or something? Or is it just something that changes on Ubuntu side?

I want to keep using my modem on my Windows XP machine too, so I don't want to change things on the modem itself.

Can someone explain what changing the firmware in this case means? Other solutions?

I hope my question is not too abstract.

Cheers,
Jan.

---

### Post by caravel on 2006-10-21
No, it gets installed to /lib/firmware and is not actually flashed to the device itself.

You have the "temperamental" green modem to you may find it difficult.  I remember going through this with the silver modem about 2 years ago on Mandrake 9.1.  I did get it working once but never again.  That guide is alot better than the guide I used though so it may be worth a try.  There is also a complete shell script about that is supposed to do it for you, but I'd avoid that one.  Make sure you use the right firmware for the green modem mentioned in the guide or the alternative firmware in the link if all else fails.

Good luck.

p.s. when I ran this in the past my silver modem still worked perfectly under windows aftwerwards, and still does (I have two of the black square modems (the newest ones) a silver one and a red 1, but I've only tried this on the silver one).

---

