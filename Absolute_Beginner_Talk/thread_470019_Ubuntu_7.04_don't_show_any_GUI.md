---
title: "Ubuntu 7.04 don't show any GUI"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by RafagaX on 2007-06-10
Hi everyone! I installed Ubuntu 7.04 32 bit edition and when I try to boot it, it doesn't show any GUI, It shows the loading splash screen and the progress bar, and when it finish to load it only shows a black screen that slowly becomes a white/black horizontal stripes design,then slowly back to a black screen. I got the same problem with te live CD default boot options, that means with the default VGA option in the live CD options.

---

### Post by taurus on 2007-06-10
Sounds like X is having a problem with your graphic card.  Boot into recovery mode and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```
And if you are not sure about a question, just use a default and use **vesa** driver for your graphic card for now until you get X up and running.  Then, you can install a driver for it.  

What graphic card do you have anyway?

---

### Post by RafagaX on 2007-06-10
I have a HP dv6220 laptop, with an AMD Turion 64 x2 processor, and a NVIDIA GeForce Go 6150 integrated graphic card

---

### Post by RafagaX on 2007-06-10
Thank You Very Much taurus! I solved my problem with your suggestion.

---

