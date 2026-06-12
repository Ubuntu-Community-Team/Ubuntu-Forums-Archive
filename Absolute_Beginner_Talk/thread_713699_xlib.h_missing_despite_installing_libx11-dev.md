---
title: "xlib.h missing despite installing libx11-dev"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by gcbs on 2008-03-03
xlib.h does not exist anywhere on my computer. i've got gutsy. I generally like looking for solutions before posting, but almost every xlib.h issue i found was solved when the user installed libx11-dev, which i have. i've also installed xorg-dev and xlibs-static-dev, as that solved the problem for all others - still no luck.
thanks for reading and for any help i may recieve

---

### Post by oakgrove on 2008-03-03
Maybe try sudo apt-get install libxcb-xlib0-dev libax25-dev

I'm not sure off the top of my head but one of those packages may have xlib.h.  Also bear in mind that libx11-dev has Xlib.h with a capital X not xlib.h with a lower-case x.

---

### Post by gcbs on 2008-03-03
thank you! I knew it was something ridiculous like that... capital X, indeed. the simplest things always escape me.

---

