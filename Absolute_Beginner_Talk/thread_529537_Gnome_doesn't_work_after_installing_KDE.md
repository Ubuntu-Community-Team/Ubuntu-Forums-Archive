---
title: "Gnome doesn't work after installing KDE"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-19
I have downloaded Ubuntu Feisty LiveCD, but then I decided to try KDE, so I typed in> sudo aptitude update && sudo aptitude install kubuntu-desktop I am very happy with my KDE desktop but when I tried to enter Gnome a Mac OS X theme pops up and taskbars with no icons. What should I do?:(

---

### Post by joe.turion64x2 on 2007-08-19
Have you tried to reboot the machine?

---

### Post by mikecomua on 2007-08-19
YES. I deleted  GNome and installed it again but  nothing works.

---

### Post by Immolatus on 2007-08-19
What is the hardware??

If you had gnome installed first ,you should remove KDM from  synaptic. Standard install with gnome as default uses GDM. If when you installed KDE it asked you which to use (KDM or GDM) you probably chose KDM which is now conflicting with GDM. so just remove KDM should be fine.

---

### Post by mikecomua on 2007-08-19
Thanks!

---

### Post by sailor2001 on 2007-08-19
ctrl/alt/backspace and then look for the options at bottom left and "sessions"

---

