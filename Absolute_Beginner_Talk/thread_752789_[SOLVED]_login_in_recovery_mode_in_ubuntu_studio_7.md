---
title: "[SOLVED] login in recovery mode in ubuntu studio 7.10 i386"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by famous3warriors on 2008-04-12
Please help on this matter.  installed Ubuntu Studio 7.10 i386 on my notebook.  It started the ubuntu studio screen finishes with line underneath and then my screen goes blank.  It stayed like that for a good 5 min. then I tried it again and the screen went blank.  How do I login in recovery mode or is there something else I can do to fix this problem.  It is a fresh install.  Thanks for your help.

---

### Post by warbread on 2008-04-12
> **famous3warriors said:**
> Please help on this matter.  installed Ubuntu Studio 7.10 i386 on my notebook.  It started the ubuntu studio screen finishes with line underneath and then my screen goes blank.  It stayed like that for a good 5 min. then I tried it again and the screen went blank.  How do I login in recovery mode or is there something else I can do to fix this problem.  It is a fresh install.  Thanks for your help.

You need to get into the Grub menu.  When you boot your computer, you'll see some text saying something like "Booting to Grub menu... 3... 2... 1...".  Press ESC at this point and you'll see recovery mode, as well as the non-RT kernel and it's recovery mode.

---

### Post by famous3warriors on 2008-04-12
Thanks warbread  I found out that my xserver-org was not installed.  I need to install do I have to do a complete reinstall of the system

---

### Post by joshrobinson on 2008-04-12
i posted a reply in the other thread you were asking in, i think you spelled the command wrong
its xserver-xorg not xserver-org

---

### Post by famous3warriors on 2008-04-12
thanks for your help it worked wonderfully.  I was able to log on just fine now just doing updates.
I really do appreciate the help.

---

### Post by joshrobinson on 2008-04-12
your welcome, glad you got it working

---

