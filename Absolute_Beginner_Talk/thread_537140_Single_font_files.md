---
title: "Single font files"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by alican timur on 2007-08-28
How do i install single font files? I've put them in /usr/lib/share/fonts but no software recognises it..

---

### Post by s26c.sayan on 2007-08-28
Run in a terminal :
**fc-cache -v**
as well as
[B]sudo fc-cache -v


[/B]Also, make sure that /usr/lib/share/fonts is mentioned as a font path and uncommented in your /etc/X11/xorg.conf

---

### Post by Perfect Storm on 2007-08-28
If it's for a single user for gimp/open Office etc. etc. and you don't need the fonts systemwide, create a folder called **.fonts** then move your font files to that folder.

---

### Post by alican timur on 2007-08-28
okay. got it. there's this another thing.

these are screenshots from my and my friends msn clients at the same time. I've installed ms true type fonts, but there's still these huge differences in fonts. why is this like this? and how can i solve this issue?

---

### Post by Perfect Storm on 2007-08-28
Personally I would say it looks better in the Ubuntu.

Have you tried change font rendering? (system ---> preferencers ---> fonts)

---

### Post by alican timur on 2007-08-28
i like win ones better.. i tried that. it's not it.

---

