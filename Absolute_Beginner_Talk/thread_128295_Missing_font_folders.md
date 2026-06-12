---
title: "Missing font folders?"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by lynmtan on 2006-02-11
hi all! already tired searching the forums for the series of problems i encountered in upgrading to breezy. so, i decided to post this one.

at boot-up, the system says, "setting up general console font failed".  the Xorg.0.log listed some font directories that do not exist and said that 'fonts.dir' is not found or is not valid. i checked the directory and saw that the fonts.dir doesn't exist.  how can i install the general console font from the terminal?  i can't get x to work after an upgrade to breezy. i also manually upgraded the kernel coz the old one panicked.

thanks in advance...

=========
solved it already:  sudo apt-get install xfonts-base

---

