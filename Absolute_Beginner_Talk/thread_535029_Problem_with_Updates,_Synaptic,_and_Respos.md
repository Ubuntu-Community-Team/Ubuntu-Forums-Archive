---
title: "Problem with Updates, Synaptic, and Respos"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-08-26
I have a problem, as I stated.  I tried to install Virtual Box, but I stopped after I installed all the stuff, because the installation was getting no where.  However, the .deb window wouldn't close, so I ignored.  Eventually, I had to turn off my computer so I could fix my wireless card.  Now, I get this error when trying to install updates, and when starting Synaptic Package Manager:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

Also, whenever I am in Add/Remove, when I try to check something, I get the loading signal, and it never stops, thus I am not able to install something from there.  Could someone please help me with this problem?

---

### Post by Fonon on 2007-08-26
Please help!  I really have no idea on how to fix this!

---

### Post by Fonon on 2007-08-26
Bump for help.  I really need help!

---

### Post by some_random_noob on 2007-08-26
This is probably a problem with VirtualBox. You've somehow corrupted VirtualBox and now it's attempting to reinstall itself whenever you go into your package manager. Try "sudo apt-get uninstall virtualbox" (In the command line) and try to kill VirtualBox. Then maybe that error will go away. I'm no expert, but it sounds like VirtualBox has messed up your computer a little bit. Try and remove it somehow.

---

