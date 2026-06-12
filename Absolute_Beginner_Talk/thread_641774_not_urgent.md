---
title: "not urgent"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2007-12-15
When I had dapper, I really liked the way ubuntu showed you what it was doing while it was booting. it just meant  that on the off chance that ubuntu crashed (yes I did use the words crash and ubuntu in the same sentance) I could tell the technition what it was doing when it crashed. Is it possible to get the same splash screen for gutsy?

Thanks heaps

---

### Post by barbedsaber on 2007-12-15
its still not super urgent, but I would like to keep this on the first page

---

### Post by wormser on 2007-12-15
Since it is not urgent I will post the answer later.... not.

You can remove the splash screen in /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

Change:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=[COLOR="Red"]**quiet splash**[/COLOR]
```

to

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=
```

That method will remove the boot screen for all kernels.  You can remove the boot screen from a single kernel by removing the quiet splash from the end.

---

### Post by rsambuca on 2007-12-15
You can also just remove the word quiet, and then have the splash and the text scrolling at the bottom.

And please wait for a day or two prior to bumping your threads.  If you require immediate assistance, then use the IRC channels.

---

