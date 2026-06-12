---
title: "HAL failed to reactivate PCMCIA slot after hibernation?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by heiko.nolen on 2007-05-14
As of right now, my wireless card (which used to work flawlessly) has stopped even giving the green light for power. My theory is that HAL failed to reactivate the PCMCIA slot after a hibernation, and I just can't figure out how to reactivate it manually.

I've tried ejecting and inserting (both physically and using cardctl / lspci), but the only report I get is: "no card".

My feeling is that if I could run a line to set the power status of the PCMCIA slot to whatever state means active, then all I'd need to do is to plug in the card manually...

Help?

---

### Post by oilchangeguy on 2007-05-14
have you tried restarting the computer?

---

### Post by heiko.nolen on 2007-05-14
restarted, plugged card in and out, lspci and get the response "no card"

---

