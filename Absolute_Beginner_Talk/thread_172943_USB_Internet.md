---
title: "USB Internet"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-09
Okay, I'm not sure if anybody will be able to help me with this, but here goes.  I installed Ubuntu on an old junker HP yesterday.  This fricken thing is so ancient it doesn't even have an ethernet card, or anything of the like.  I have a modem (westell 6100) that will allow for USB internet connections.  However, I tried connecting it to the computer to find no results.  I think I need a USB driver or something like that, but am not sure.  Is any such thing available for Linux?  I really love this OS so far - been playing around with it for hours now - but want nothing more than to connect to the internet with it.  Thank you in advance for any ideas you might have.

---

### Post by gr0kzer0 on 2006-05-09
Have you tried wvdial? Read its man pages. It will detect modems on your system. I had a mobile phone connected by a USB data cable when I ran wvdialconf and it detected the phone as a modem, so a USB modem may be fine.

Wvdial came with the Breezy default install so you should have it already, ask Synaptic.

---

