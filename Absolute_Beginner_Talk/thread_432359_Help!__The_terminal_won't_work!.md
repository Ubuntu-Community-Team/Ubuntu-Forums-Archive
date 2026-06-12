---
title: "Help!  The terminal won't work!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-05-03
I just upgraded to Feisty Fawn.  I remember there was an error during the installation process, but I didn't think much about it.

Now, when I try to open a terminal (using a created shortcut), the screen will suddenly look weird for a second, and then the system loads, but I'm suddenly logged off.  It also froze once when I tried this.  Can someone please help me fix the terminal?

---

### Post by Seisen on 2007-05-03
You might need to create a new shortcut for the terminal. Can you still access the terminal from Applications>Accessories>Terminal. Also do this to make sure that it got all the packages when you upgraded.

```
sudo apt-get update
sudo apt-get dist-upgrade
``` or you can use aptitude whichever one you prefer.

---

### Post by nanotube on 2007-05-03
in the meantime, you could also use one of the virtual consoles. ctl-alt-f1 through ctl-alt-f6 switches you to one of the vtys, and ctl-alt-f7 gets you back to the gui.

if you can't figure out the problem with gnome-terminal, you could also try installing one of the very numerous other terminal emulators. there's xterm, konsole, aterm... just to name a few. they are all just a "sudo aptitude install" away.

---

### Post by bobplano on 2007-05-03
haha but again konsole and xterm and stuff an aptitude away requires the terminal. you could just get them at packages.ubuntu.com if you need them though and synaptic isn't working

---

### Post by nanotube on 2007-05-03
> **bobplano said:**
> haha but again konsole and xterm and stuff an aptitude away requires the terminal. you could just get them at packages.ubuntu.com if you need them though and synaptic isn't working

that's where the VTYs come in. just a quick ctl-alt-f2 away. :)

---

### Post by purplearcanist on 2007-05-04
I tried the terminal from Applications>Accessories>Terminal, and it appears to work.  I guess it only does this when I try using a shortcut for the terminal.  Anyway, thanks for the location of this terminal.:)

---

