---
title: "wine install and xlib6g-dev"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by stil on 2007-07-31
Hi there

I've run ./tools/.wineinstall, and at the end it suggested I should have xlib6g-dev as wine did not build with X support. I've looked through packages.ubuntu.com but not found it. Is this really necessary?

Also, typing 'wine' in the console while in the wine directory returns 'command not found' even though *its right there?* :confused:

btw, no internet = no apt-get... no "just apt-get ***" posts please

---

### Post by ramjet_1953 on 2007-07-31
Probably what it wants is:

libx11-6
libx11-dev

Worth a try

Regards, 
Roger :cool:

---

### Post by stil on 2007-07-31
Giving it a shot now. Needed about a dozen packages to install libx11-dev :o

---

