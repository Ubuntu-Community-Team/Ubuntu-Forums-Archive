---
title: "Edgy update - artifacts under cursor"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by steve.horsley on 2007-02-11
After updating yesterday, I get a horizontal bar under the mouse pointer. It moves with the pointer, and it seems to be associated with the pulling down menus. This is on an ATI card with fglrx driver.

Anyone else found this?

---

### Post by steve.horsley on 2007-02-12
Removing the fglrx driver removes the artifact. I'll live without fglrx.

---

### Post by marx2k on 2007-02-12
You wouldn't be able to show a screenshot of what you mean, by any chance would you?

---

### Post by iramhernandez on 2007-02-12
I"m having the same issue with ATI drivers after updating kernel and recompiling proprietary drivers.  Mouse cursor is jacked up.

---

### Post by steve.horsley on 2007-02-13
I can't give you a screen shot because taking a screen shot turns the cursor (and the atifact) off. I attach a mock-up drawing of roughly what it looked like. The colour of the bar chganged according to what I clicked on sometimes.

---

### Post by cheenky on 2007-02-22
i have that exact same problem, thanks I'll try removing the drivers

---

### Post by Enigmatic on 2007-03-09
> **cheenky said:**
> i have that exact same problem, thanks I'll try removing the drivers

Same thing here, X700 card. Hope this gets bug status soon.

---

### Post by Enigmatic on 2007-03-09
It appears that this may be caused when hardware acceleration isn't properly detected/enabled according to a Launchpad post. Now I'll have to go and see how I can enable it, since everything was working fine before Edgy for me.

Edit: I enabled 3d acceleration and it seems to have disappeared.

---

