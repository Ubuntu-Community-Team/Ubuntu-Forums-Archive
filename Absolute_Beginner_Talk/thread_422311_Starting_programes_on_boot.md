---
title: "Starting programes on boot"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-04-25
I would like to start Skype when I boot the system. This is how it worked in Windows can this also be done in Ubuntu?

---

### Post by igknighted on 2007-04-25
Assuming you are using gnome, go to System->preferences->sessions and add skype to the startup list.

---

### Post by avanrens on 2007-04-25
That work fine thank you.

---

### Post by Drewski on 2007-04-25
How is this accomplished manually? Where is the startup list stored, somewhere in /etc?
I'm curious because I'd like to learn how to use Linux and not just the GUI.

---

### Post by igknighted on 2007-04-25
> **Drewski said:**
> How is this accomplished manually? Where is the startup list stored, somewhere in /etc?
I'm curious because I'd like to learn how to use Linux and not just the GUI.

No, it's in your home folder.  I have no idea about gnome, but in KDE its in .kde/Autostart.  You can create a script and add applications to start, or if you are lazy like me you just symlink the command from /usr/bin (although the script is the way to go).  In one of the hidden folders in your home directory (probably .gnome) will be a similar folder/file to add stuff to.

---

