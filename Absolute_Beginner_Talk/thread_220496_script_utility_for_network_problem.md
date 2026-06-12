---
title: "script utility for network problem?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Rockyhead on 2006-07-21
For some weird reason my NIC-card wants to hang on to IP-addresses, and the only way I can get the connection to work, is always writing

sudo dhclient -r eth0
sudo dhclient eth0

in the terminal. Putting aside the matter of me not understanding why this is, it would be nice if I could simplify things a bit. Is there a way that I could make some kind of "script-tool-icon-thingy" on the desktop, which would rock my world and make the flowers blossom by simply double-clicking it?

Please, don't laugh... I have no programming experience:(

---

### Post by moma on 2006-07-21
Have you tried to fix the basic problem with your network connection. Why it hangs on IP-adresses?

Anyway, this is how to make a script.
In a terminal window
$ [COLOR="Green"]cd $HOME[/COLOR]

Make a new file
$ [COLOR="Green"]gedit fixnetwork.sh[/COLOR]

(type [COLOR="Green"]kate fixnetwork.sh[/COLOR] if you run Kubuntu)

and add these 3 lines into that file:

[COLOR="SeaGreen"]#!/bin/bash 
gksudo "dhclient -r eth0"
sudo dhclient eth0
[/COLOR]

Save the file and make it executable
$ [COLOR="Green"]chmod +x fixnetwork.sh[/COLOR]

Create a shortcut-icon on the desktop.
Press right-mouse-button on the desktop and choose "Create launcher".
Mark the checkbox "[x] Run in a terminal".  Drag & drop the icon onto the main toolbar (panel) and let the flowers blossom.

EDIT: You can also run the script in a terminal window. Do
$ [COLOR="Green"]cd $HOME[/COLOR]
$ [COLOR="Green"]./fixnetwork.sh [/COLOR]

---

### Post by Rockyhead on 2006-07-21
Thanks man, I actually think I understood that....

Yes, I have tried to solve the prob. It happens in WinXP as well (dual-boot), so it would suggest something hardware-based. Blaah... I'm just baffled:confused:

---

