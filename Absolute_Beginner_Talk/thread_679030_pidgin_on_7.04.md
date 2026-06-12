---
title: "pidgin on 7.04"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by pazzyjazzy on 2008-01-26
i wanna install pidgin on ubuntu 7.04 .. but i get this 
The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.2.1-z) but 1:2.3.1-1~getdeb1 is to be installed
          Depends: libsilc-1.0-2 but it is not installable
E: Broken packages

tell me what to do .. 
i hav done everything the why in which it was written on most of the google results .. help

---

### Post by Mr. Eddy on 2008-01-26
upgrade to ubuntu 7.10 and you have pidgin by default ;)

---

### Post by pazzyjazzy on 2008-01-26
lol ..i kno that .. but i hav 256mb ram .. so i think i will go with 7.04 only till my dad gets me a new ram..

---

### Post by benste on 2008-01-26
256 MB should be fine for Gutsy without Compiz (my sister does use it also with compiz and 256 MB Ram)

---

### Post by Mr. Eddy on 2008-01-26
as you can see from the errors you get, it's a package problem. pidgin uses new packages that are not available in the 7.04 repos. So this will be difficult

How did you tried to install pidgin? did you download it from the site?

---

### Post by Red Shift on 2008-01-26
Which version of Pidgin do you want to install?  From where did you get it?

Which repositories do you have enabled?

If you use Synaptic:

Synaptic --> Settings --> Repositories

Universe will need to be enabled (checked) to install libsilc-1.0-2

[http://packages.ubuntu.com/feisty/libs/libsilc-1.0-2](http://packages.ubuntu.com/feisty/libs/libsilc-1.0-2)

---

