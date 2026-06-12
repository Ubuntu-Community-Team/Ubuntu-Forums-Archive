---
title: "Switch Video Cards"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2007-02-05
Ok so I have an ATI 9250 card in my PC and I want to install Linux but the thing is I want to install it so it uses my integrated video chip. I know that means flipping the Monitor Cable in the back but I can put up with it. Is it possible to do that so that Windows will use the video card and Ubuntu won't?

Thanks for the help.

---

### Post by ed-j on 2007-02-05
> **PPAAUULL said:**
> Ok so I have an ATI 9250 card in my PC and I want to install Linux but the thing is I want to install it so it uses my integrated video chip. I know that means flipping the Monitor Cable in the back but I can put up with it. Is it possible to do that so that Windows will use the video card and Ubuntu won't?

Thanks for the help.

Caution: Reply from Novice!

This sounds possible, but, I think you would have to specify which graphics device you are choosing to use in 6.1 as well as moving the monitor cable. There are Binary Drivers for ATI from 8500 upwards in Add/Remove if you feel like giving that a try.

Are you worried that Ubuntu 6.1 won't support the ATI card?

---

### Post by PPAAUULL on 2007-02-05
I am not worried that it won't support it in fact I have tried it with my card it is just that there is so much trouble in getting it to work and it doesn't even work proporly I rather switch the cable and have fully functional.

---

### Post by mlind on 2007-02-05
I think he/she wants to know if it's possible to choose which gfx card to use at runtime. I'm quite sure it's possible. I've never tried it with gfx cards, but with several sound cards there's no problem.

I'm not sure what's the correct way to accomplish though, maybe blacklisting modules or hiding i/o resources, dunno. X.org may offer some more sophisticated way to do this also.

---

### Post by ed-j on 2007-02-05
> **PPAAUULL said:**
> I am not worried that it won't support it in fact I have tried it with my card it is just that there is so much trouble in getting it to work and it doesn't even work proporly I rather switch the cable and have fully functional.

Ok. You will have to specify which graphics device you want to use in Terminal, and as a novice, my way of doing this would be a risk and you would need to know which PCI configuration number to set ( on mine it's PCI:3:0:0 if you see what I mean).

Best I can do! Other help will follow.

---

### Post by ed-j on 2007-02-05
A question I forgot to ask: Did you download the ATI drivers from their website or did you activate the drivers within Ubuntu?

---

