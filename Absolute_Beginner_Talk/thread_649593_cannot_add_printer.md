---
title: "cannot add printer"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-12-25
hello,

after the latest kernel update, my laptop no longer recognizes my network printer.  i've tried adding it through the System-Administration-Printing dialog, but the printer is never actually added.

any ideas?

thanks,

-steve

---

### Post by %hMa@?b&lt;C on 2007-12-25
can you still access the printer if you boot into an older kernel?

---

### Post by stevieb on 2007-12-25
no older kernels are showing up in menu.lst

---

### Post by stevieb on 2007-12-25
i found a 2.6.20-15 and booted into it, but still no dice.  also my usual kernel is lowlatency, and i've already tried the standard version of that as well.

---

### Post by stevieb on 2007-12-26
problem was solved by "complete" removal (incl. config files) and reinstallation of cupsys. thanks to all who took the time to help!!

---

