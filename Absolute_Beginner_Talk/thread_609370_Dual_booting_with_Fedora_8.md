---
title: "Dual booting with Fedora 8"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-10
How is GRUB going to handle it?  will it recognise it right away or am I going to need to work for it

---

### Post by K.Mandla on 2007-11-10
You might check this thread, or its parent forum.

[http://ubuntuforums.org/showthread.php?t=607301](http://ubuntuforums.org/showthread.php?t=607301)

---

### Post by amaroKer on 2007-11-10
I usually copy the lines from the old /boot/grub/menu.lst into the one with the active bootloader to boot whatever is already installed.  Works for me.  The installer assumes that you want to chainload another bootloader if you add any entries in the boot window.  This works for windows partitions, but only if you have specially set up your boot loader to chainload in the past will it work for any linux distro.

---

### Post by louieb on 2007-11-10
What is installed now FC or Ubuntu?
The Ubuntu installer should add an entry to its GRUB menu for FC. - don't know how good the FC installer would be at picking up Ubuntu.
Sometimes the installer doesn't  add a entry for the other distro. but its possible to do it manually.  I prefer to chain load or use the configfile statement to load the 2nd, 3rd ... distro's  grub menu.
Good stuff here: [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

