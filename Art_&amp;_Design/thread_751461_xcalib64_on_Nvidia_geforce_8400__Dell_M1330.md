---
title: "xcalib64 on Nvidia geforce 8400 / Dell M1330"
date: 2008-04-10
forum: Art &amp; Design
---

### Post by nick_edwards on 2008-04-10
I'm trying to install colour profiles on my Dell M1330, running Ununtu 7.10 64bit version. I've tried using both xcalib and argyll dispwin and neither have any effect on the display no matter what profile I load. (I'm presuming by loading a profile the display will change as with windows) 
further more when I run dispwin which brings up a colour test patch and flips thorough a couple colours, that works fine however when the screen is supposed to darken and lighten nothing happens.
has anyone managed to get it working with the same or similar setup to me or encountered similar problems?

xvidmode is installed and working

---

### Post by jcornuz on 2008-04-10
Hi there,

Try tying: 
[INDENT]xgamma -gamma 1.5[/INDENT]
on a terminal.

With xcalib comes bluish.icc which is handy for testing (it turns your screen blue). Does 
[INDENT]xcalib /path/to/bluish.icc[/INDENT]
has any effect?

You may want to check if the Nvidia driver is supported by xcalib / dispwin... I don't have Nvidia, so there isn't a lot more I can do to help.

Take care,

Joel

---

### Post by nick_edwards on 2008-04-11
Solved - kind of, I discovered it works with sudo, now to fix the permissions, anyone have any idea how to do this?

---

