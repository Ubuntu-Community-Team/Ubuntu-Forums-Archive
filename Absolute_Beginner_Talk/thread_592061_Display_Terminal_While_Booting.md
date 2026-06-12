---
title: "Display Terminal While Booting"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by bostonca on 2007-10-26
I was wondering if there was a way to show the terminal while Ubuntu is starting up. So instead of seeing the Ubuntu logo and a status bar I want it to display everything that it is doing. Thank you.

---

### Post by swoll1980 on 2007-10-26
install start up manager from getdeb.net lets you do all kinds of things with your boot options

---

### Post by Baby Boy on 2007-10-26
> **swoll1980 said:**
> install start up manager from getdeb.net lets you do all kinds of things with your boot options

That's a handy tool to have, but can you recommend something like that which allows you to choose what programs will automatically run when Ubuntu starts?

---

### Post by nick_h on 2007-10-26
Edit your /boot/grub/menu.lst file and remove the boot options quiet and splash.  I think you can also add verbose.

You can also edit the options at boot time by pressing "e" on the grub entry.

To make the changes permanent for all kernels you will have to change the defoptions line in the menu.lst file and then re-run update-grub.

---

