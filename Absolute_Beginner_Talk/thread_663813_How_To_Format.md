---
title: "How To Format"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by mirulmuffs on 2008-01-10
i want to clean things up. how to format ubuntu? i mean how to make things like default? without reinstalling ubuntu. i wish it will requires only terminal. 

i am dualbooting ubuntu 7.10 and vista.

---

### Post by Rocket2DMn on 2008-01-10
There really isn't any way to "revert" to the original settings without doing a reinstall.  Is there something in particular you want to clean up?
For future reference, the best way to keep the system "clean" is to install everything using Synaptic or apt-get.  This lets the system manage your packages rather than having nasty installs from source all over the place.

---

### Post by Hospadar on 2008-01-10
there's not really a way to make things just like the install without re-installing.  you could consider moving your home directory to a seperate partition (the entire /home, not just /home/<your name>), re-installing, and during the installation mount that home partition as home.  this will clear out any old software installations without messing with your home directory. (all your user settings and data would stay that way)

Otherwise, try just uninstalling packages you don't need, and look through your home directory and delete configuration files and folders you no longer need (they are hidden by default ctrl-H in nautilus or "ls -a" to show them, they all begin with a '.' like .config)

Another thing you can do as well, is if you must install things from source, use "checkinstall" to install them (which replaces the "make install" command) this allows you to use synaptic to remove software you built from source, as it builds a .deb package out of your source "make" installation.

---

### Post by skroops on 2008-01-10
Just install from cd again.  Make sure not to choose the option to format the partition that you are installing on.  The grub installer should find windows and work the same as before.  If you have multiple linux data partitions you will have to choose which one will be home, root, etc. and then choose not to format it as well.  It will prompt to let you know you are installing on an unclean partition.  It will not be exactly like default but should be close.  You will want to choose a different username or rename your home folder before you reinstall as well.

---

