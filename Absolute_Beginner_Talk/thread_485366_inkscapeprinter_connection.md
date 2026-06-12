---
title: "inkscape/printer connection"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by donquixo1929 on 2007-06-26
Inkscape will not connect to printer (canon pixma iP3000).  Also whatever I "copy" in inkscape will not "paste" into another application.

Does inkscape have any way of outputting to a plotter/cutter?  Roland pcn900.

---

### Post by p_quarles on 2007-06-26
First, if you want to use the default printer in Inkscape, you have to delete the text in the "print destination" line of the dialogue. 

Second, you can't copy/paste scalable vector graphics into applications which don't handle them. The two easiest ways to get them into another program are: 1) save the file "as" the kind you want (postscript, GIMP, OpenOffice Draw, PDF, etc.); 2) Download the .svg extension for the GIMP (available in the repos). 

Hope this helps.

---

