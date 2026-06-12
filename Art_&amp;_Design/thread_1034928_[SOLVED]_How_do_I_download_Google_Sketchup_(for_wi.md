---
title: "[SOLVED] How do I download Google Sketchup (for wine) ?!?"
date: 2009-01-09
forum: Art &amp; Design
---

### Post by desconocido on 2009-01-09
When I go to [http://www.google.com/sketchup/download/](http://www.google.com/sketchup/download/)
and click on "Download Google Sketchup 7"
the resulting page [http://www.google.com/sketchup/download/gsu.html](http://www.google.com/sketchup/download/gsu.html)
just contains

[SIZE="4"]Download Google SketchUp 7[/SIZE]
Please make sure your system meets these requirements prior to downloading Google SketchUp.

From looking at the page source, I suspect it works out that I am trying to download from a system it does not support and won't let me.

Do I have to find a Windows machine for the download or is there some easier way?

Thanks in advance,

Bob

---

### Post by meborc on 2009-01-09
just tried clicking on the second ling you gave... it gives me the licence and a download button... choice between win and mac version... i choose mac and click download... and it comes (ubuntu 8.10 + firefox 3.0.5)

---

### Post by desconocido on 2009-01-09
I tried changing the language to Spanish. It only offers version 6 but still behaves the same way - tells me to check the system requirements and won't let me download.

I am using the same version of Firefox as you and 8.04 Ubuntu.

---

### Post by desconocido on 2009-01-09
Just tried deleting cookies as well. No luck

---

### Post by ColBuendia71 on 2009-01-09
Went straight through for me as well. That's really odd. Here's the direct download link anyway. Just open up a terminal and:

```
cd (whatever directory you want it to d/l to)
wget http://dl.google.com/sketchup/GoogleSketchUpWEN.exe
```

And that should do it.

---

### Post by desconocido on 2009-01-10
I contacted the SketchUp Help Center and they said

> Thank you for your note. We've had other users report this issue, although
they were using XP rather than Linux. As a result, the problem may not
actually be related to your operating system. To troubleshoot, please
attempt to download Google SketchUp Pro 7 from the link below:

[http://sketchup.google.com/support/bin/answer.py?answer=115548](http://sketchup.google.com/support/bin/answer.py?answer=115548)

and that worked fine for me. Thanks everyone.

---

