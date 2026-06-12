---
title: "Bittorrent Uninstall"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by SAMW on 2007-03-31
I wanted to use bittorrent in ubuntu. I couldn't find it in my system or pull it up in terminal even though it and the gui were installed. I got the deb from the bittorrent website and i was going to install it but the deb installer said that it conflicts with the bittorrent already installed in my system. I was going to uninstall the bittorrent client that was already installed on my machine, but in order to do that, synaptic said that i would have to also uninstall ubuntu-desktop. This didnt sound like a good idea to me so, should i uninstall ubuntu-desktop or is that an error with my system/ my system is dependent on bittorrent.

---

### Post by K.Mandla on 2007-03-31
It's okay to uninstall ubuntu-desktop; it's just a metapackage that labels everything else -- like a bottlecap. If you take it out, everything else is still there. So yes, you can uninstall the default bittorrent package, and it's okay that ubuntu-desktop goes too.

---

### Post by pppetter on 2007-03-31
Although you CAN uninstall ubuntu-desktop, does not mean that you SHOULD. If I were you I would use the bittorrent client already installed, or get some other client that has more functionality, like Ktorrent. 

To find out were your client resides, you can for example check its properties in Synaptic, theres a full list with all the files that comes with the bittorrentclient package. My guess is that is hangin around in /usr/bin.

---

