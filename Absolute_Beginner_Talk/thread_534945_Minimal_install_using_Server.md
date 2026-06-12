---
title: "Minimal install using Server"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
If I do the server install, how do I get the MINIMAL install? Like, I only want the GUI interface installed..I don't want openoffice, the music apps and other stuff.

Is this the command I type in?
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal

I want basic func like synaptic manager, gnome etc. I will install the applications I want manually using synaptic.

---

### Post by oilchangeguy on 2007-08-25
if you do the server install, there is no gui. you've already had at least one thread on this subject. why is this hard? simply un-install what you don't want/need!

---

### Post by Dr Small on 2007-08-25
Here is the minimal cd:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by kerry_s on 2007-08-25
> **pencil86 said:**
> If I do the server install, how do I get the MINIMAL install? Like, I only want the GUI interface installed..I don't want openoffice, the music apps and other stuff.

Is this the command I type in?
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal

I want basic func like synaptic manager, gnome etc. I will install the applications I want manually using synaptic.


[B]sudo apt-get install xorg gdm synaptic gnome-core
reboot(ctrl+alt+delete)
select gnome in the session menu and log in
open synaptic and keep building
[/B]

if your going through all that trouble, why not go lighter?
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

