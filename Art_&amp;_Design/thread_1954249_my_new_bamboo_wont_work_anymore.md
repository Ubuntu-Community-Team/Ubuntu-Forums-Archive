---
title: "my new bamboo wont work anymore?"
date: 2012-04-07
forum: Art &amp; Design
---

### Post by p.wolf on 2012-04-07
so i got my tablet the other week, got it working, but last night i plugged it in, the lights came on but it wouldn't work. Whats wrong? is it something with the drivers? what should i do?

---

### Post by Favux on 2012-04-07
Hi p.wolf,

What release of Ubuntu are you using?  Which model Bamboo?
```
lsusb
```
How did you get it working?  Did you allow a kernel update through Update Manager?


Edit:  Alright I found your earlier post.  A Bamboo Connect (Pen) on Oneiric, correct?  I think the kernel was recently updated on Oneiric.  If so that would have broken your new wacom.ko.  That's because the new kernel's module directory doesn't have the new wacom.ko in it.  Instead it has the old non-working wacom.ko.  So you recompile the wacom.ko like you did before.  It'll take just a few moments now that you've done it before.

---

### Post by p.wolf on 2012-04-07
i see, thank you very much : ) sorry for the slow reply i haven't been having a great day. But thank you for the help and i will do as advised, take care : )

---

