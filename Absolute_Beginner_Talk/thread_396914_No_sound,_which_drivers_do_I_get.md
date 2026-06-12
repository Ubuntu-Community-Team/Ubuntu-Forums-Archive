---
title: "No sound, which drivers do I get?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2007-03-30
Here is the output of lspci:
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

I've searched around, but I don't know what drivers to get for this.

Any help/suggestion/comments?

---

### Post by MikeyP on 2007-03-30
hi - probably way off the mark here, but quite often the sound gets muted by default... worth checking if you haven't already... Mike

---

### Post by Mardok45 on 2007-03-31
The sound's on.

---

### Post by eljalill on 2007-03-31
Hm. Never heard of an ATI sound card and also not fond it on the Internet.
If you have a desktop you could open the case and look at the card, since it should be written on the card, what exactly it is, 
if you have a Laptop, you could either look on the Internet or ask the manufacturer, what sound card you exactly have, or post it here, and see if someone knows.

Or, of course if you are dual booting, and the sound is working fine in windows, look at the hardware manager there to find out.

And with the sound you have to not only see that the Master is on. Already happened to me  (and others), that the Master (the one seen in the Panel) was on, and I didn't have any sound, because all the others were muted. Double click on the icon in the panel or type "alsamixer" in a terminal to check.

---

