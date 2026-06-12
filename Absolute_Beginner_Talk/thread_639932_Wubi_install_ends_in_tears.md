---
title: "Wubi install ends in tears"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by ironjade on 2007-12-13
After creating a dual boot with Vista and Ubuntu via the Wubi installer and using it quite happily for a while, Ubuntu suddenly froze. With the only choice being to turn off the power and reboot, I  got the message that no operating system could be found.
As a result I had to reinstall Vista (which attempted to take out my external HD incidentally) and give up on Ubuntu. I'd like to reinstall it via Wubi but don't want to go through all that again. 
What could've caused the freeze and is there a way of avoiding it? :confused:

---

### Post by Dark_Stang on 2007-12-13
So after reading up on what Wubi is, I'd really recommend using an Ubuntu CD and just repartitioning the hard drive. You really don't have anything to fear since it's a fresh install anyway.

The error was probably it messing up the windows boot loader.

---

### Post by PinkFloyd102489 on 2007-12-13
If you use EasyBCD to make a backup of the Vista bootloader, you can add Ubuntu to the Vista bootloader using EasyBCD and keep everything as normal.

---

### Post by ironjade on 2007-12-13
Thanks for your fast replies. I may have another crack at it tomorrow (when I'm awake).:)

---

