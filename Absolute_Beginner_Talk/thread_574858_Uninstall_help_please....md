---
title: "Uninstall help please..."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-10-13
Hey everybody,
I have Ubuntu on a dual boot on a second hard drive with Windows XP.  I would like to uninstall ubuntu (to add a different distro) and remove GRUB as well.  Last time I just formatted the partition and GRUB kept giving me error 23. I want to eliminate Ubuntu and GRUB and just want XP to boot normally.  Dell 3000 Dimension, Ubuntu 7.0.4 desktop edition.  I CANNOT boot into ubuntu.  It wont let me.  Thanks

---

### Post by taurus on 2007-10-13
Maybe you want to have a look at this thread, [http://ubuntuforums.org/showthread.php?t=574725](http://ubuntuforums.org/showthread.php?t=574725).

---

### Post by defrex on 2007-10-13
To sum up: format the Ubuntu partition; pop in an XP CD and go into recovery mode; then run the command *mixmbr**.

That should restore Windows to master of the boot.

*Edit: uhh... ya, not sure why I wrote *mixmbr*... Taurus is right, it's *fixmbr*

---

### Post by taurus on 2007-10-13
*fixmbr*

---

### Post by aheicher on 2007-10-13
excellent, thank you

---

