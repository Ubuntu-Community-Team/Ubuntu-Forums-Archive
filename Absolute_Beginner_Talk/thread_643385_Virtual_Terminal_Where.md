---
title: "Virtual Terminal? Where?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Crushyerbones on 2007-12-17
Did the virtual terminal change on Gutsy for some reason? I've been searching around and every thing I see about not being able to use them is related to some graphics glitch. If I hit ctrl+alt+Fsomething I can see a flashing "_" at the top left corner of the screen (Kind of like the one we used to see all the time when windows 98 booted up). But I can't do anything with it. Do I need to enable something in order to use it?

---

### Post by annda on 2007-12-17
you mean it's just a flashing cursor, not a login prompt? there is nothing except the flashing underscore? on **all** virtual consoles?

i can't help you if that is the case, but i'm still asking those questions so that others with more expertise have more info and can jump in with specific tips.

---

### Post by macogw on 2007-12-17
Do you have framebuffer enabled?  Gutsy doesn't load the framebuffer module in the initrd (why??? this bug and the fix were reported well ahead of release!) so you have to take the framebuffer stuff out of your boot parameters or create a new initrd image.

---

### Post by Crushyerbones on 2007-12-17
> **annda said:**
> you mean it's just a flashing cursor, not a login prompt? there is nothing except the flashing underscore? on **all** virtual consoles?

i can't help you if that is the case, but i'm still asking those questions so that others with more expertise have more info and can jump in with specific tips.

Yes to all.
> Do you have framebuffer enabled? Gutsy doesn't load the framebuffer module in the initrd (why??? this bug and the fix were reported well ahead of release!) so you have to take the framebuffer stuff out of your boot parameters or create a new initrd image.

How would I do that? :S Please...

---

### Post by macogw on 2007-12-17
In your /boot/grub/menu.lst is there something like vga=300 at the end of any of the kernel lines?  Use "gksu gedit /boot/grub/menu.lst" to look.  If there is, take that off the lines and save

---

### Post by Crushyerbones on 2007-12-17
Just the VGA part? ok... be right back

---

### Post by macogw on 2007-12-17
You'll have to reboot for it to take effect.

---

### Post by jw5801 on 2007-12-17
For the record the bug report is [here](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910). The fix is about halfway down the page.

---

### Post by Crushyerbones on 2007-12-17
It seems to work now, Only had to restart X (I think that's what ctrl alt backspace does) because i saw a blank screen after loging on..


Other than that... all's fine :D Thank you

---

