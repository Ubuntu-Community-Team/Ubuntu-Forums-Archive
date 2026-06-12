---
title: "Modem Detected by Ubuntu, But Can't Here it Dial"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by HercuLeeZ on 2005-07-09
Greetings all,

A friend of the family was having severe virus and malware problems on XP, so I offered to let them try Ubuntu. After installing it, their modem WAS detected, and I see it in the connections listing. However, when I try to connect with it, I don't here a dial-tone and cannot connect to any Internet resources.

Is there a fool-proof means of ensuring that the modem is working properly? Can we use 'pon' or something?  This is my first adventure with Dial-Up and Linux.

Thanks!
Herc

PS: They are at a rural cottage, so dial-up is the only option

---

### Post by Digitallysick on 2005-07-09
are you sure the modem is not a "winmodem" certian modems are made for windows only, i see them in HP's, Compaqs etc, you might want to post excatly what type of modem it is.  (brand?)

---

### Post by polo_step on 2005-07-09
Yeah, that's my guess here, too.  Though I now have DSL, up until recently I was on dialup and went through a lot of hassle with various modems in various Linux distros. I was never able to get an internal software modem working with Linux, though I got a number of internal hardware modems working OK.  Externals are a snap. 

There are a number of software Winmodems that are supposed to work (somewhat) with Linux, but I've not had luck with them.  I also think the lists I've seen are outdated.

I also couldn't hear the modem in this OEM Linux box, though it worked (after a fashion!), but as it turned out it was a cheap "riser" modem with no internal speaker anyway, so the joke was on me.  A modem without a speaker is about as dead useless a proposition as I can imagine.

Assuming you have a functioning, Linux-compatible modem, make sure you have the initialization commands for speaker & loudness in the modem configuration.

What happens when you "query" the modem?  Does it give up any data?

---

### Post by az on 2005-07-09
Try:

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

Start with the modem subpage and use scanmodem to identify your modem chipset.  Many or most winmodem have some linux support.

---

