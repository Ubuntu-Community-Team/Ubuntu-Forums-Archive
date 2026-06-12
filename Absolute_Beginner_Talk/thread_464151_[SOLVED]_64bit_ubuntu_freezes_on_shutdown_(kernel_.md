---
title: "[SOLVED] 64bit ubuntu freezes on shutdown (kernel panic) shutdown sound plays in endl"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-06-04
first off i know this might be better off in the 64bit user forum, but people seem to answer to post faster in the beginner forum and as i'm a beginner with 64bit ubuntu and other people might have the same problem, i posted it here. well here we go.

this problem only exists for me when using the 64-bit version of ubuntu i386 does not have the problem.
so on 64-bit the problem started with kernel panic on boot right after grub menu. --> computer freezes capslock led starts blinking. totally unresponsive have to use reset to reboot.
in recovery mode computer starts normally, startx gets me to my graphical desktop. no problems. shutting down in recovery mode works too.

in normal mode after solving the start freeze bug (found the solution for the boot-freeze problem on launchpad) i now have the same problem when shutting down. --> computer freezes capslock starts blinking and the shutdown sound is stuck in a endless loop.

i've read somewhere that this might be a problem with the xorg-fglrx drivers. I'm using the restricted drivers not the ati manually built ones. Before i start building the drivers manually i wanted to ask if anyone already found a solution to this problem? PLZ help because my 64-bit system is definatly running faster the the i386 (y i switched).

by the way for people with same problem: boot freeze solution:
add vga=792 to default and kernel options in /boot/grub/menu.lst
or turn off splash

---

