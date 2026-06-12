---
title: "disabling startup scripts"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by The Reepr on 2007-06-24
I need to diable and delete a startup script becuase it was for beryl and xgl, but now everything on my screen is scrambled. I need to do it through terminal. is there a way to wipe out all commands? I don't know what the name of the command is that I typed in.

---

### Post by w4ett on 2007-06-24
Start by selecting Gnome as your default from the "session' button on the login screen when you boot, and select it as your default.   You can then delete Beryl via the Synaptic Package Manager.

---

### Post by The Reepr on 2007-06-25
but I can't do anything graphical. That's my problem. all graphics and text are distorted

---

### Post by w4ett on 2007-06-25
> **The Reepr said:**
> but I can't do anything graphical. That's my problem. all graphics and text are distorted

 Fron the command line type:

sudo dpkg-reconfigure xserver-xorg

this will bring up the semi-graphical interface to configure your xserver

up and down arrows move the cursor

spacebar marks selections, enter confirms.

Select the open source driver for your video card and resolution and refresh rates....complete the operation and restart x.  Then.... select Gnome as your default from the "session' button on the login screen when you boot, and select it as your default. You can then delete Beryl via the Synaptic Package Manager.

---

