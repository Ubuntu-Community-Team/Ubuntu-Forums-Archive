---
title: "I cannot start a gnome terminal session"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Claudia Frers on 2007-02-22
When i click on the terminalicon, a window starts up and dissapears right away.
If i use a run command and type gnome-terminal, the same happens.
If I use the run command and type konsole, a shell starts. Why does a shell not start
when i click on the terminal icon or when i try to run gnome-terminal.

I have tried to reinstall gnome-terminal using apt-get to no avail.

Thanks

---

### Post by louis_nichols on 2007-02-22
I suspect it's because the permission in some configuration files may be wrong. I suggest you use nautilus to set permissions for all files and folders in your home folder to read-write by owner. Also, make sure the owner is your username. Use the "Apply permissions to enclosed files" on the folder properties page for this

You might need to do this from Nautilus in root mode. Make sure you start it with *gksudo nautilus*.

---

### Post by szf on 2007-02-22
Back in May 2006, I was a Fedora user and ran an YUM update that subsequently killed all my terminal sessions. The culprit then was a package called vte (vte.i386 0.12.1-1.fc5.1). After much work I managed to 'thunk' the xterm and vte RPM packages back to default - only to be bitten again a couple of months later... So I came to Ubuntu.

The question is, have you run any update/upgrade that included terminal-related packages lately?

---

### Post by jackrobinson on 2007-02-22
> **Claudia Frers said:**
> When i click on the terminalicon, a window starts up and dissapears right away.
If i use a run command and type gnome-terminal, the same happens.
If I use the run command and type konsole, a shell starts. Why does a shell not start
when i click on the terminal icon or when i try to run gnome-terminal.

I have tried to reinstall gnome-terminal using apt-get to no avail.

Thanks
use the run command and type **xterm** and hit enter. From xterm, launch **gnome-terminal**. Then paste the errors here.

---

