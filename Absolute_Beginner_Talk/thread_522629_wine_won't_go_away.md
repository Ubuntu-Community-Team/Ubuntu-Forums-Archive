---
title: "wine won't go away"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-08-10
OK, so I installed Picasa, and noticed that it runes a small program called Wine System Tray.  I didn't like this, so I uninstalled Picasa, but the little program won't go away!  I can't even close it!  What do I do to get this stupid program to go away!

---

### Post by mysticmatrix on 2007-08-10
Well Picasa for Linux is not a true native version as it uses a technology called WINE(Wine is not a Emulator) to run Windows version of Picasa on linux. (Read more on [www.winehq.com](www.winehq.com)).
You can get rid of that application by doing a simple reboot, or if you are too concerned about it, just open your system monitor and kill the process named 'wineserver'

---

### Post by limberlegs on 2007-08-10
Yeah, I rebooted and it seemed to take care of things.  So how can I check if the program is gone entirely?  I'm sure it's not a big deal to have it sitting around on my system, but I'm kind of nitpicky and I would like to know how to get rid of it for good.

---

### Post by vexorian on 2007-08-10
you might need wine eventually...

---

### Post by original_jamingrit on 2007-08-10
see what happens when you enter ```
sudo apt-get remove wine
``` into the terminal.

Also, when using the Synaptic Package Manager (System->Administration->Synaptic) press the Status Button, and then select "Installed" from the list to see all of the things you have installed through Synaptic.  (Mind you, this won't necessarily include programs and packages not installed through Synaptic.)

---

### Post by bigboy_pdb on 2007-08-10
If you installed the program using wine, it should be in the ".wine" folder in your home folder (press CTRL-H to see the hidden files). If you don't want any of the programs that were installed using wine then you can just delete the ".wine" folder.

---

