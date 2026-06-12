---
title: "inskape pen reset style"
date: 2010-03-01
forum: Art &amp; Design
---

### Post by ItalOz on 2010-03-01
I have tried to use one of the path effects for inskape with the bezier pen tool. The "Pattern Along Path".
I played around with it a little and then I wanted to go back to use the bezier pen tool as usual.
But now I cannot go back to the original style.
Let's say that I want the pen to draw lined with no fill and a black stroke of 10 points and every time I use the tool again I have the  effect listed in the path effects editor, and I have to remove it manually, plus the pen never comes back to the style.
I have of course tried setting in the object properties "create new objects with:" but it does not take into account.

Any clues?

Ah and where is the .inskape directory that contains the preference files in Ubuntu 9.10?

Cheers

[edit]
I have found the answer to the first question, there is a mode menu when you select the pen tool I had it set on clipboard.
Thus every time I was drawing a new bezier curve inskape was taking a shape to apply to the pattern from the clipboard, I had to set it to none and then also the preferences dialogue worked and resetted the tool style.
I still don't know where the .inkscape dir is

---

### Post by rax0 on 2010-03-01
There's no .inkscape in the Home directory, instead go to /home/YOUR_USER_NAME/.config/inkscape

Hope it answers your second question ;)

---

### Post by ItalOz on 2010-03-18
Thanks
this is part of the changes with Ubuntu 9.10 compared to 8?

---

