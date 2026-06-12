---
title: "Changing Grub so Windows boots first"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2007-07-19
I am using both Windows and Ubuntu on my computer at work. Because others may use this computer, I want it to boot to Windows by default instead of Ubuntu. I had done this before quite awhile ago, but have forgotten how to do it. Thanks.

---

### Post by ThrobbingBrain66 on 2007-07-19
Some people might tell you to make Windows the first entry in your menu.lst file.  While this works, it could present problems later on when/if your GRUB is updated.  So to do this, we'll open up the menu.lst file:
```
gksudo gedit /boot/grub/menu.lst
```
Almost right at the top of the file you'll see a section labeled '#default num'

We need to find out what number your windows partition is in the grub and then put that number at the end of this section where it says 'default     0'.

The big thing that you have to remember is that numbering starts from 0, so the first entry would be 0, not 1.

---

### Post by Daveth on 2007-07-19
the last post (not my bit as i had not thought it through properly when I posted!!!) gives some recent links  to follow up:

[http://ubuntuforums.org/showthread.php?t=501678](http://ubuntuforums.org/showthread.php?t=501678)

---

### Post by S29K on 2007-07-19
Post removed...

---

