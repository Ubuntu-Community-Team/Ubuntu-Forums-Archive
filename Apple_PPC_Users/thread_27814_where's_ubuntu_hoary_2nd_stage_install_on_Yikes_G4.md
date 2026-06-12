---
title: "where's ubuntu hoary 2nd stage install on Yikes G4?"
date: 2005-04-17
forum: Apple PPC Users
---

### Post by accozzaglia on 2005-04-17
I seem to have exhausted my Google search leads to solve this independenttly.  I couldn't, so hindight input from other Ubuntu users is welcome.

I've overhauled my old Power Mac G4 350MHz PCI "Yikes!" box to run Ubuntu 5.04 distro as my primary system.  For the time being, it's the only system installed on this box.

Aside from my system only being able to install with the *video=ofonly* toggle enabled from Open Firmware (the standard "install" results in an incompatible scan frequency with my CRT), the installation CD process seems to install smoothly and without any outstanding concerns.  Upon completion of *first stage* install, the process asks that the Hoary CD be removed and upon reboot, the second stage will pick up and complete the rest of the install process.

Except that my system won't do that.

When I reboot at the prompt, the startup is fine, but instead of an installer script automatically beginning of the *second stage* of the install, I only get a consolee prompt for login.  Nothing more.  Whether I login as root or as a regular user, I'm left to my own devices, basically.  Which is fine, I'm sure, for some, but I'm not yet a Linux maven/guru/expert with a decade of experience using this stuff.

I did try to manually apt-get the components for Xserver-xpro, but that configuration didn't work as hoped.  So, this brings me back to why the installation process didn't walk into a second stage upon restart.  I've reinstalled using standard install, expert mode and server, but the outcome is the same each time: console prompt with nothing more.

It's either this or YDL, and I want to give Ubuntu a chance.  :)

---

### Post by Rxke on 2005-04-18
looks like the 1st generation G4s, both Yikes! and sawtooth, are finicky machines... maybe have a look at this=
[http://ubuntuforums.org/showthread.php?t=24957&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=24957&page=1&pp=10)

---

