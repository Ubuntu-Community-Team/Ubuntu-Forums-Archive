---
title: "pdf to html?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-18
any1 know of a program for this?

---

### Post by aysiu on 2006-07-18
How about [pdftohtml](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pdftohtml&searchon=name&subword=1&version=all&release=all)?

---

### Post by Ben Sprinkle on 2006-07-18
ok thanks

---

### Post by Dominus Suus on 2006-09-15
When I try to install it apt-get wants to remove cups-pdf, which is just as important.  Why is there this conflict?

---

### Post by aysiu on 2006-09-15
> **Dominus Suus said:**
> When I try to install it apt-get wants to remove cups-pdf, which is just as important.  Why is there this conflict?
Maybe it has to do with your repositories list?

---

### Post by Dominus Suus on 2006-09-15
No, I figured it out.  pdftohtml is in the poppler-utils package (so it's installed through sudo apt-get install poppler-utils) then I can run pdftohtml normally.  I suppose pdftohtml package, which is in the Universe, is depreciated or something.

---

### Post by Dominus Suus on 2006-09-29
General information about getting pdftohtml to work:
Package pdftohtml refuses to install because it conflicts with a bunch of packages including:

bluez-cups
cups-pdf (my pdf printer which I cannot live without)
cupsys
cupsys-driver-gimpprint
cupsys-driver-gutenprint
hplip
poppler-utils

...which is (supposedly) fine because poppler-utils contains a pdftohtml binary which, from what I can tell, is identical to the pdftohtml package.  There's a problem with version 0.5.1 of the package where >pdftohtml foobar.pdf produces an empty html document with lots of horizontal rules ("<hr/>").  This problem has been fixed, at least on my machine, in version 0.5.4 of the poppler package.

---

