---
title: "html2pdf"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-12-13
I'm attempting to convert a page on a website into a pdf document. I know about just printing it to a pdf printer, but I need to do this from within a script. Could someone recommend a way to accomplish this?

---

### Post by gakudva on 2007-12-13
While printing from browser - select Postscript print option.  Make sure, you select "Print to file" checkbox.  This will create a postscript file.  Now, start command line and try:
```
ps2pdf <postscriptfilename> <targetpdffilename>
```

---

### Post by nhandler on 2007-12-13
The issue is, I want to do this completely in a script. That means I need to find a way to do the "Print to File" step from within a script, and not from firefox.

---

