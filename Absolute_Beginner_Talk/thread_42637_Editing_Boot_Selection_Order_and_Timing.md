---
title: "Editing Boot Selection Order and Timing"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by Vicsun on 2005-06-18
I'm dual-booting Ubuntu with WinXP, and want my computer to boot to WinXP by default (not Ubuntu), as well as decrease the timer from 10 seconds to something more reasonable. What (and how) do I do to GRUB to do this?

Also, please explain the concept of  repositories to me (or link me to a document that does it), as they seem kind of important, and yet I found it hard to find anything on them.

---

### Post by poofyhairguy on 2005-06-18
[QUOTE=Vicsun]I'm dual-booting Ubuntu with WinXP, and want my computer to boot to WinXP by default (not Ubuntu), as well as decrease the timer from 10 seconds to something more reasonable. What (and how) do I do to GRUB to do this?[/QUOTE]

You need grubconf.
 
Download this file:

[http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

put it in your home directory. Close synaptic and open a terminal.

Type this:

> sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb

run the program with this command:

> gksudo grubconf

[QUOTE=Vicsun]Also, please explain the concept of  repositories to me (or link me to a document that does it), as they seem kind of important, and yet I found it hard to find anything on them.[/QUOTE]


[http://www.ubuntuforums.org/showpost.php?p=215368&postcount=5](http://www.ubuntuforums.org/showpost.php?p=215368&postcount=5)

[http://www.ubuntuforums.org/showpost.php?p=211999&postcount=3](http://www.ubuntuforums.org/showpost.php?p=211999&postcount=3)

I would read those in that order.

---

