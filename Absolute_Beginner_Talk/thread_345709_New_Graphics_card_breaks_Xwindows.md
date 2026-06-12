---
title: "New Graphics card breaks Xwindows"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by linux_believer on 2007-01-24
I installed a new card and since it is not configured I only get a command prompt. Is there a GUI I can use to configure it or some type of automated program? (Hey the CD will auto configure the driver if I boot from it.) Just looking for a way to get me back to a gui so i can install the correct driver. Or how can I :easily do it from the command line.

I'm installing an Nvidia card

Please advise

---

### Post by arochester on 2007-01-24
At the prompt input: sudo dpkg-reconfigure xserver-xorg

This should start a text wizard to reconfigure. If you can't answer any questions go with the suggested answers.

---

### Post by jbayone on 2007-01-24
You can also try the "nv" driver when doing the dpkg-reconfigure xserver-xorg, then use the envy script to install the correct driver for your card.

---

