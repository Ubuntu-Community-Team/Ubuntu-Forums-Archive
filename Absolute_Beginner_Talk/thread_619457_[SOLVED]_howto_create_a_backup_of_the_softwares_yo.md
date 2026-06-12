---
title: "[SOLVED] howto create a backup of the softwares you have on your system"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by sourcemorph on 2007-11-21
i have a painfully slow net connection in my college, and with a lot of effort i have downloaded a lot of softwares frm the net... now i plan to reinstall ubuntu. i know that all the .deb files are there in /var/cache/apt/archives and i can create a backup of it.

but when i reinstall my system i'll have to manually install each .deb package, plus i'll have to install the dependencies before the actual package and its really frustrating with so many packages.

is there a software that can backup everything and automatically install the softwares that i need.

or is there a way that i can install softwares in add/remove applications by putting a dvd as a source and not the internet?

please help...

---

### Post by nick_h on 2007-11-21
Have a look at [APTonCD](http://aptoncd.sourceforge.net/).

---

### Post by sourcemorph on 2007-11-21
i have used aptoncd.. what it does is .. it makes an iso image of all the packages present in /var/cache/apt/archives ...

i dont think thers an option to restore the packages automatically.

---

### Post by sourcemorph on 2007-11-22
yeah thanks.. i found an option in AptonCD which automatically selects the dependencies..

---

