---
title: "Changing themes crashed Ubuntu"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by dcbtfoabaaposba7 on 2007-03-29
Hey, i was changing the icons and themes of my ubuntu and my computer froze. When i restarted my computer Ubuntu doesnt get passed the splash screen. Recovery mode works and i deleted ~/.themes and ~/.icons thinking it would fix the problem, but it hasntl. What can i do to get my ubuntu working again? thanks.

---

### Post by dbbolton on 2007-03-29
try this:

first, boot into "recovery mode" from GRUB

when you get to the terminal, 

```
sudo dpkg-reconfigure xserver-xorg
```basically, just press enter the whole way through. this will reset your graphical interface, and hopefully solve your problem !

---

### Post by cowlip on 2007-03-29
I posted here instead: [http://ubuntuforums.org/showthread.php?t=393432](http://ubuntuforums.org/showthread.php?t=393432)

---

