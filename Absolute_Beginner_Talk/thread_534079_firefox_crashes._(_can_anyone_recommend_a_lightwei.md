---
title: "firefox crashes. :( can anyone recommend a lightweight browser?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by jon.reeve on 2007-08-24
I'm running Xubuntu on an 950MHz / 256M RAM laptop, and have been having problems with Firefox crashing pretty frequently. It's usually when I have three or four tabs open and the system seems to be doing a lot of processing. The window freezes and refuses to redraw. At that point I usually have to run xkill, which kills the window but the process is still running, so then I have to go to the system monitor and term the process, all of which is a big hassle. Does anyone know why this happens or how to fix it? 

Also, could anyone recommend a lightweight browser that doesn't use so much of the system's resources?

---

### Post by irish_flu on 2007-08-24
I'd say that a crashy Firefox is at least somewhat rare.  Do you have any extensions ("add-ons") installed?  If so, perhaps one of them is the problem.

Likewise, some folks have issues with the "total conversion" themes; try selecting a different theme, maybe that will make a difference.

Does a certain website, r something specific (like Flash, especially) seem to be a common thread in the crashes?

---

### Post by livestockPimp on 2007-08-24
firefox IS a lightweight browser.

---

### Post by Dr Small on 2007-08-24
Swiftfox my be a suggestion, but it is just Firefox that is optimized for older processors I think. I'm using it right now.

Dr Small

---

### Post by funrider on 2007-08-24
give iceweasel a try! it is the brother of firefox without all the commercial stuff.

here is the installation step by step guide

[http://www.debianadmin.com/install-iceweasel-web-browser-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-iceweasel-web-browser-in-debian-and-ubuntu.html)

---

### Post by funrider on 2007-08-24
> **livestockPimp said:**
> firefox IS a lightweight browser.

ff has well-known memory issue, both on windoze and linux.

---

### Post by irish_flu on 2007-08-24
> **funrider said:**
> ff has well-known memory issue, both on windoze and linux.

Works fine on my Celeron 333, with 256MB of RAM.

---

### Post by Arthur Archnix on 2007-08-24
> **livestockPimp said:**
> firefox IS a lightweight browser.

Maybe at one point... but just because it's one of the greatest browsers doesn't mean it's lightweight. Opera is a good alternative with similar functionality, after that, you get into truly lightweight browsers that sacrifice features for resource usage.

---

### Post by funrider on 2007-08-24
> **irish_flu said:**
> Works fine on my Celeron 333, with 256MB of RAM.

thanks for making me doing for research. you are the lucky one but it is really a problem quite generally

[http://kb.mozillazine.org/Memory_Leak](http://kb.mozillazine.org/Memory_Leak)

if you want to keep ff, you can follow the KB instruction to tweak it.

---

### Post by irish_flu on 2007-08-24
> **funrider said:**
> thanks for making me doing for research. you are the lucky one but it is really a problem and mozilla has it stated in their knowledge:

[http://kb.mozillazine.org/Memory_Leak](http://kb.mozillazine.org/Memory_Leak)

if you want to keep ff, you can follow the KB instruction to tweak it.

Agreed, that link has some excellent tips for "trimming" memory usage in Firefox.  Keep in mind, though, that they specifically state the leaks have been fixed in Firefox 2.  A large footprint is a very different thing from a leak.  :)

---

### Post by ddrichardson on 2007-08-24
Firefox isn't light weight, [now Dillo]("http://www.dillo.org/") on the other hand...;-)

---

### Post by glotz on 2007-08-24
^Beat me to the punch mister!

---

### Post by Dr Small on 2007-08-24
An even lighter-weight browser:
```
w3m
```
and
```
lynx
```

;)

Dr Small

---

### Post by kerry_s on 2007-08-24
> **jon.reeve said:**
> I'm running Xubuntu on an 950MHz / 256M RAM laptop, and have been having problems with Firefox crashing pretty frequently. It's usually when I have three or four tabs open and the system seems to be doing a lot of processing. The window freezes and refuses to redraw. At that point I usually have to run xkill, which kills the window but the process is still running, so then I have to go to the system monitor and term the process, all of which is a big hassle. Does anyone know why this happens or how to fix it? 

Also, could anyone recommend a lightweight browser that doesn't use so much of the system's resources?


try the one straight from firefox and see if that crashes.
[http://www.mozilla.com/products/download.html?product=firefox-2.0.0.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-2.0.0.6&os=linux&lang=en-US)

just unpack it, go inside and click/execute on firefox
if that works you can just put the folder in place of the old one, don't forget to copy over the plugins.

---

### Post by glotz on 2007-08-24
Also see [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes)

---

