---
title: "I am searching for information to recompile the kernel with APCM."
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-22
I am searching for information to recompile the kernel with APCM (Adanced Power Control Managament).

I understand that this is really not distro specific, however if this has been done with Ubuntu, details and information would be greatly appreciated.

Thanks,

---

### Post by John.Michael.Kane on 2006-03-22
[http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+compile](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+compile)
[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel+compile](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel+compile)

---

### Post by ranf on 2006-03-24
Do you -- by any chance -- mean APM support?
[http://en.wikipedia.org/wiki/Advanced_Power_Management](http://en.wikipedia.org/wiki/Advanced_Power_Management)

Then you don't have to compile your own kernel.
You just add the following kernel parameters:
```
acpi=off apm=on
```

The best place for this is in "/boot/grub/menu.lst"

---

