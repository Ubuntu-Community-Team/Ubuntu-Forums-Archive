---
title: "Where are programs installed?"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by nutuubuntu on 2005-12-12
After installing programs using Synaptic or even when compiling myself I never know where they are installed to or where to find them! Sometimes a program appears in the gnome program list after installation but sometimes it doesn't. Sometimes I can just type the program name into the command line and it opens - other times it says "bash: [program name]: command not found". I have sometimes had to resort to searching the system for the bin file which sometimes is in usr/bin and others in /usr/sbin. 

This is so far my only real problem with Ubuntu/Linux ... I guess I'm just used to all programs being installed in the "programs" directory and links to them appearing in the Program list.

Can someone explain the Linux way for me?

---

### Post by Estariel on 2005-12-12
/usr/bin
should contain all executables of programs you can install with synaptic but are not necessary for the system to boot (so everything that comes with the distribution)

/usr/local/bin
should contain all executables of programs you installed yourself (self compiled stuff, etc.).

/usr/sbin
should contain all executables that are necessary for the system to boot (of course these also come with your distribution).

Edit: Concerning the GNOME menu: Everything that has a GUI and gets installed with synaptic should get a link there. If it does not, it is probably a bug. Command line tools don't get a link, since starting them from the desktop environment (and not from the terminal) does not make sense.
Everything you install manually (not synaptic) might or might not get a link in the GNOME menu - depending on what you install, and what the creator of your installer thought of.

---

### Post by 23meg on 2005-12-12
To find where exactly the files from a certain package are installed, right click the package name in Synaptic, go in to "Properties" and then the "Installed Files" tab.

---

### Post by arun.in on 2008-07-16
thanks for the info. What can I do to manually link the program in application menu.

---

### Post by bapoumba on 2008-07-17
arun.in: this thread is from 2005 and in the archive section.
If the package does not place itself in the Main Menu, you can add an applet in a toolbar or edit the Main Menu (in Preferences).
I'm closing here.

---

