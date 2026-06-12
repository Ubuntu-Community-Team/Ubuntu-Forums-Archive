---
title: "Bittorrent Clients"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-11-10
I've been using KTorrent for a while now and am rather happy with it. However, it does have a few bugs. Are there any viable alternatives (i've heard a lot about deluge and qbittorrent) that do more than Ktorrent?

---

### Post by matthewcraig on 2007-11-10
Why not join this thread:
[http://ubuntuforums.org/showthread.php?t=609055](http://ubuntuforums.org/showthread.php?t=609055)

---

### Post by Pumalite on 2007-11-10
Deluge and Azureus are others to try.

---

### Post by Raven18940 on 2007-11-10
> **intense.ego said:**
> (i've heard a lot about deluge and qbittorrent)

Tried both, and I found both more buggy than Ktorrent, and Azureus just quits every time I try to open it.  You can run Utorrent in wine.

---

### Post by Pumalite on 2007-11-10
The Azureus that comes prepackaged, opens up and closes, but the one you download from sourceforge.net works just fine.

---

### Post by Raven18940 on 2007-11-10
> **Pumalite said:**
> The Azureus that comes prepackaged, opens up and closes, but the one you download from sourceforge.net works just fine.

Too lazy to do more than "apt-get give me stuff." :p  Actually I probably try it later tonight.:)

---

### Post by Pumalite on 2007-11-10
It's a tarball that installs itself.

---

### Post by ffi on 2007-11-10
> **Pumalite said:**
> The Azureus that comes prepackaged, opens up and closes, but the one you download from sourceforge.net works just fine.

Yeah and if you place it in /opt and change the group permission to users (and add all users to the users group) it will update automatically as well and if you save the following:

[i][Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;[/i]

as /usr/share/applications//azureus.desktop you will also get a menu entry

---

### Post by Pumalite on 2007-11-10
Good to know.

---

