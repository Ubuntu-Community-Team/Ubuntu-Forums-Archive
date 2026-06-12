---
title: "Is my monitor too big?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-03
Hi

I'm thinking of getting a bigger, digital, monitor - an 19in job (16:10, and 1440x900 pixels). Only trouble is, when I look under syste>perferences>screen resolution, the maximum number of pixels seems to stop at 1280x1024.

Can I use the proposed monitor with Ubuntu.

Regards

Roger D

---

### Post by taurus on 2007-03-03
Yes, as long as you have installed a driver for your graphic card.

---

### Post by RogerD on 2007-03-03
Thanks.

Sorry, but I see, with hindsight that I've asked two questions, one in the heading and one int the text. I take it that you've answered the question in the text. So you're saying, YES, I'll be able to use the proposed monitor, subject to installing the necessary drivers.

I have Navida on-board graphics, and I obtained the drivers via Automatix.

Do you still think I'm going to be OK?

Regards

Roger D

---

### Post by taurus on 2007-03-03
Yes, X should be able to run that resolution, widescreen.  You probably just need to edit /etc/X11/xorg.conf to add that new resolution in there and you are all set.

---

### Post by RogerD on 2007-03-03
Fine.

I'll go ahead with the new monitor

Many thanks for your help.

Roger D

---

### Post by Scorpuk on 2007-03-03
I have had my ubuntu box connected to my mates HD LCD TV and that was ok, after adjusting the xorg.conf to add in its max resolution of 1366 x 768. That was with an Nvidia card with automatix driver installation.


So you should have no probs at all.

---

