---
title: "bitorrent clients fighting"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by KeithO on 2005-10-17
I had Hoary and installed Azureus and it worked fine.  Then upgraded to Breezy and now the preinstalled bitorrent program is taking over Azureus as my default and I can't figure out how to get Azureus back as my default. Ideas?

---

### Post by Murgle on 2005-10-17
find a torrent file and right click on it then go to properties, go to the Opens with tab, if the program you want to be default is on the list then simply check it's radio button, if click the add button and select it off the list, if it's not on the list then click the use custom command button and add it, then make sure that the radio button for the program you want is selected and that is your default program

---

### Post by KeithO on 2005-10-17
using demonoid thats not an option.  right clicking and going to properties opens just gives the file address and "opens with".

---

### Post by KeithO on 2005-10-17
also i should mention that azureus opens up about a minute later but the torrent file isn't listed in the queue.  takes it a long time to load for some reason.

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=KeithO]I had Hoary and installed Azureus and it worked fine.  Then upgraded to Breezy and now the preinstalled bitorrent program is taking over Azureus as my default and I can't figure out how to get Azureus back as my default. Ideas?[/QUOTE]

this command in terminal:

> sudo apt-get remove bittorrent

tell it yes at the next question. Trust me.

---

