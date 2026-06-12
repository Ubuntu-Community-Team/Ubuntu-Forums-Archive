---
title: "changing screen resolution"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by confudler on 2006-11-29
During set up I accidentally allowed the program to believe my monitor could display 1024*768 resolution. I temporarily plugged in another monitor and changed the resolution once it had loaded but this only applies once I am logged in. I can log in blind but would like to change the default to 800*600. How can I do this?

---

### Post by an.echte.trilingue on 2006-11-29
log into a terminal and run this command:

```
sudo dpkg-reconfigure xserver-xorg
```

and then you can select all the screen sizes you do or do not want to have available.  After you have done this, restart your X server with CTRL+ALT+Backspace.

Good Luck

-mat

---

### Post by confudler on 2006-11-29
thanks, a bit scary (I just okayed all the options until i got the one i wanted) but it worked.

---

