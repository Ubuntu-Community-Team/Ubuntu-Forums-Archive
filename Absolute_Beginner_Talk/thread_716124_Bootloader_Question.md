---
title: "Bootloader Question"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by D3M0L1$H3® on 2008-03-05
Is there a way to turn of the 5second countdown on the boot loader?
(So that It waits until I choose something, no matter how long that may be)?

---

### Post by kyphi on 2008-03-05
In a terminal type ```
sudo gedit /boot/grub/menu.lst
``` and alter the numeral to the right of the entry for "timeout".  That will give you a delay in seconds.

---

### Post by forestpixie on 2008-03-05
found this after a bit of a mooch

[http://ubuntuforums.org/showpost.php?p=711661&postcount=8](http://ubuntuforums.org/showpost.php?p=711661&postcount=8)

which seems to suggest that getting rid of the number stops the count down - however I don't know if it works, so if you try I'd suggets backing it up

```
sudo cp  /boot/grub/menu.lst  /boot/grub/menu.bak.0503
```

---

### Post by dstew on 2008-03-05
I think if you comment out timeout (put a # in front of it) the menu will stay up until you do something.

---

