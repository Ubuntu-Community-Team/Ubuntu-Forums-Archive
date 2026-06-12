---
title: "Disabling SMP"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bazar on 2007-03-24
I have been having heat problems with my laptop
(Compaq, AMD sempron 1.8g processor).
I have seen some posts in another forum here that
said the problem might be with the SMP support
in the 2.6.17-11-generic kernel and that SMP
should be disabled for my particular type of laptop.
Other than having to custom compile a kernel, is
there anyway I can disable SMP, or is there another
kernel available somewhere that already has SMP 
disabled?

---

### Post by igknighted on 2007-03-24
You can pass a "nosmp" kernel option.  Add it to the end of the line that starts "kernel /boot/..." in you /boot/grub/menu.lst file.  You will need to use the sudo command to edit it.

I might have the syntax wrong on that kernel option, but I know one exists... can anybody else verify the syntax?

---

