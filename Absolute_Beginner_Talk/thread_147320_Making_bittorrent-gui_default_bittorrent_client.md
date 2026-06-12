---
title: "Making bittorrent-gui default bittorrent client"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by goober99 on 2006-03-20
Since I am usually downloading several torrents, the Gnome bittorrent client that comes with Ubuntu is not adequate for me, so I used Synaptic to install bittorrent-gui. When I open a torrent file, it still opens in the Gnome client though. How do I make bittorrent-gui the default client?

---

### Post by mustang on 2006-03-20
Are you opening it in your browser or downloading it and then opening it?

If the former, assuming you're using firefox, 

Edit->Preferences->Downloads->View and Edit Actions

If the latter,

right click on the torrent file->properties->open with->add

---

### Post by orko3001 on 2007-08-31
> right click on the torrent file->properties->open with->add

Bittorrent-gui isn't on the list - I have installed with synaptic but it's not there. How do I add it to the list?

Cheers

---

### Post by Harpoon on 2007-08-31
right click on the torrent file->properties->open with->add
 
Look down toward the bottom and find "Use a custom command" and type btdownloadgui

---

### Post by ts51 on 2007-08-31
dont steal music lol

---

### Post by orko3001 on 2007-09-01
> **Harpoon said:**
> right click on the torrent file->properties->open with->add
 
Look down toward the bottom and find "Use a custom command" and type btdownloadgui

I then clicked on the torrent file but nothing happened :confused: If I right click on the file it gives me the option "btdownloadgui" but only opens with BitTorrent :(

---

### Post by quixotic-cynic on 2007-10-06
As far as I can tell the btdownload-gui is just a really basic client and I am not sure it is easy (or possible?) to queue stuff. Deluge torrent works a bit better [(deluge-torrent.org)]("deluge-torrent.org") if you can be bothered to try something else.

Edit: version 3.4.2 is current in the repos, apparently queuing was introduced in 3.9.1...

---

