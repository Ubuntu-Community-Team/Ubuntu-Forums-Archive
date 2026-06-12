---
title: "how to completely remove wine"
date: 2014-08-28
forum: Any Other OS
---

### Post by manuleka on 2014-08-28
after installing playonlinux and wine... i decided to remove them... running sudo apt-get purge only removes playonlinux but wine doesn't seem to be removed at all...

help please...

Elementary OS Freya

---

### Post by ajgreeny on 2014-08-28
You could try reinstalling wine then purging it; that should do it, I think.
 Alternatively try using synaptic package manager, which you may have to install first, assuming it is available for EOs Luna x64, which I have never heard of, but which I assume is a debian/ubuntu derivative.

You will also need to remove the hidden .wine folder in your home, as that will never be removed by any package management action.

---

### Post by manuleka on 2014-08-28
thank will try it asap... don't tell me you haven't heard of Elementary OS? Best elegant buntu derivative in my little experience in Linux...

update:
i managed to remove them....

went through my /usr/bin folder found wine/winecfg/wintricks etc in there... so did a
```

sudo apt-cache search wine

```
it revealed i have wine1.4-i386 and wine1.6-i386

so i purged wine1.4-i386 and it didn't do anything but when i purged wine1.6-i386 it removed a whole bunch of wine stuff... i also did a purge on winetricks and it seems like everything needed removing (ones i can spot) are gone :)

---

### Post by ajgreeny on 2014-08-29
Yes, of course I have heard of Elementary OS; I just didn't recognise your naming of it, and I have never seen nor used it.

Perhaps I must give it a try.

---

