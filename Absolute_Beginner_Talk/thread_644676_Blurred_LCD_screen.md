---
title: "Blurred LCD screen"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by corripops on 2007-12-19
I am running Ubuntu Gutsy on my laptop, I booted up with my Flatron LCD screen so that it bypasses my laptop screen and uses the flatron and I can set the resolution to the flatron's resolution which is 1280 x 1024 at 60hz. However the screen still is slightly blurred.
Can anybody suggest a solution?

Thanks:)

Corripops

---

### Post by weblordpepe on 2007-12-19
Create an entry in /etc/X11/xorg.conf for the exact resolution  / color depth / refresh rate that you want. Reboot/restart X and you should be in business.

---

### Post by mahiyar on 2007-12-19
I do not understand. At whatever refresh rate or sizes why should the screen be blurred?

---

### Post by weblordpepe on 2007-12-20
hmm. i dunt know. fonts perhaps?

---

