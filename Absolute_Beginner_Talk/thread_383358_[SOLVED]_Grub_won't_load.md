---
title: "[SOLVED] Grub won't load?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-03-13
I installed ubuntu from the live cd last night and got it all working, went back to windows to make sure, then back to ubuntu. Everything was fine and dandy. But this morning when I got up, grub was gone. Gone! When I booted up, the install cut right to the windows boot, with nothing in between except black. It's like some person came in and eraesed the grub boot files. I suspect it might have been the boot/grub/menu.lst file, as I edited it to make windows the default boot and shortened the wait time to 5 seconds. But I can't get to it from the live cd version, so it reamins a mystery. What's my problem?

---

### Post by overdrank on 2007-03-13
> **rouge568 said:**
> I installed ubuntu from the live cd last night and got it all working, went back to windows to make sure, then back to ubuntu. Everything was fine and dandy. But this morning when I got up, grub was gone. Gone! When I booted up, the install cut right to the windows boot, with nothing in between except black. It's like some person came in and eraesed the grub boot files. I suspect it might have been the boot/grub/menu.lst file, as I edited it to make windows the default boot and shortened the wait time to 5 seconds. But I can't get to it from the live cd version, so it reamins a mystery. What's my problem?


HI you might try this link.
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Hope this helps. Good luck!

---

### Post by louieb on 2007-03-13
Get this and you can edit the /boot/grub/menu.lst file from windows.
Do be careful. [http://www.fs-driver.org/](http://www.fs-driver.org/)
BTW: check to see that hiddenmenu is commented  out.

---

### Post by rouge568 on 2007-03-13
> **paul capps said:**
> HI you might try this link.
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Hope this helps. Good luck!

Thanks - it worked!

---

