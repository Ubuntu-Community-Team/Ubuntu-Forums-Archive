---
title: "printer problem"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by lloydsharons on 2007-08-29
I am using Ubuntu 7.04 and when I do a printer install it recognizes my Lexmark Z730 and suggests  a dirver.  I do the install and the printer will only load the paper part way before stopping anot making any attempt to put ink on paper.  According to my research my printer is a postscript printer and should not need a driver.

---

### Post by tchoklat on 2007-08-29
... therefore, print using the ctr P command and select the post script driver and see if that works for you!

---

### Post by asmoore82 on 2007-08-29
> **lloydsharons said:**
> I am using Ubuntu 7.04 and when I do a printer install it recognizes my Lexmark Z730 and suggests  a dirver.  I do the install and the printer will only load the paper part way before stopping anot making any attempt to put ink on paper.  According to my research my printer is a postscript printer and should not need a driver.

Ubuntu has a strong "across the pond" heritage where A4 paper is the standard.
So, it will default to A4 paper almost no matter what you do ...
This setting seems to be stored in the file "/etc/papersize"

so, *_remove_* the printer, then *_carefully_* run these commands in a terminal ...

```
~ $ sudo -s
~ $ echo "letter" >/etc/papersize
~ $ exit
```

After that, re-install the printer and test print.

(To figure this out, I had an HP laser priner with a screen ... so the printer kept saying "load A4 Paper")

---

