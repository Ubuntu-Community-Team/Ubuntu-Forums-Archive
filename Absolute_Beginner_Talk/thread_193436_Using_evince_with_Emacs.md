---
title: "Using evince with Emacs"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Snodgrass on 2006-06-10
Emacs views dvi files with xdvi. Can it be taught to use evince instead? :-k

---

### Post by pchachte on 2006-06-10
Here's one way (using the command line):

Install Auctex (i.e., sudo apt-get install auctex)
Run Emacs (emacs &)
Look on top menu: Command --> texing options --> pdfmode (C-c C-t C-p)

This will allow you to view the latex file as a pdf using xpdf, which you need to install.   (i.e., sudo apt-get install xpdf).

I'm not sure how to tell emacs to use evince instead of xpdf (I actually think xpdf is faster and more suitable for this purpose).  You might look at:

[http://www.emacswiki.org/cgi-bin/wiki/PdfTeX](http://www.emacswiki.org/cgi-bin/wiki/PdfTeX)

---

