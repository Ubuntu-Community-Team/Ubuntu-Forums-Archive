---
title: "PDFLaTeX"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-19
I used a text editor in Windows to create TeX files, then a program called PDFLaTeX to create PDF files from them.  I want to do something like this in Ubuntu, but the command 'pdflatex' isn't recognized in the terminal.  In windows, I would create my TeX file, then write 'pdflatex example.tex' in a command line and I would have my PDF.  Is there any way I can do this in Linux?  I have tried Google and such, but the only answer I got was that pdflatex is usually installed by default on Linux systems, which doesn't seem to be the case here.  Can anyone help?

Thanks for your help, I appreciate it.

---

### Post by ow50 on 2005-08-19
[packages.ubuntu.com](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=pdflatex&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386) tells me it's a part of tetex-bin package.

To install a tex system you should probably install the following packages:
tetex-base
tetex-bin
tetex-extra
latex-ucs

---

### Post by amcavoy on 2005-08-19
Wow, that was a lot easier than I had thought.  All I did was install those packages and it works!

Thank you for your help.

---

