---
title: "Basic WINE question - Where to install programs with wine"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by evandec on 2006-06-01
Hello,

I am installing a program using WINE and I am curious which directory I should install it in. Is there a directory that works best?

Thanks for the help.

---

### Post by [S|G] on 2006-06-01
Wine installs everything by default under "$HOME/.wine/drive_c/". That directory is its c:\ drive, and it also creates a virtual drive z:\ which is a symlink to your root directory.

I'd install everything somewhere inside my C:\ in order to keep windows stuff sorted out from my linux stuff. But there should be no problem to install it to any directory you like inside your home folder as well.

---

