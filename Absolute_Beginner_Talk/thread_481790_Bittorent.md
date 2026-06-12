---
title: "Bittorent"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-22
Bittorent is included in the Ubuntu install. so where do i find it to launch it ?

---

### Post by NeoLithium on 2007-06-22
It's actually a command line program. If you want the graphical interface, download the gui with:
```
sudo aptitude install bittorrent-gui
```

---

### Post by Crafty Kisses on 2007-06-22
> **Ssj3_man said:**
> Bittorent is included in the Ubuntu install. so where do i find it to launch it ?

I actually like Bittornado, that's a good torrent client.

---

### Post by Ssj3_man on 2007-06-22
> **NeoLithium said:**
> It's actually a command line program. If you want the graphical interface, download the gui with:
```
sudo aptitude install bittorrent-gui
```

ok how do i remove it then?

---

### Post by NeoLithium on 2007-06-22
Remove bittorrent?  The Bittorrent GUI needs the command line version to run, it's whats' called a front end, they work together; however if you were looking to install another torrent program, you can remove bittorrent completely with
```
sudo aptitude remove bittorrent
```

---

### Post by Quintin Riis on 2007-06-22
There is a python GTK client installed by default with Ubuntu.  

The best client for Unix is rtorrent, bar none.  It's available in the repositories.  

User Guide: 

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

---

### Post by i0Null on 2007-06-22
I personally use Deluge, it is a really fast client that shows all your torrents in one window and it integrates itself really nicely with the gnome desktop.

---

### Post by FleetAdmiral74 on 2007-06-22
> **Quintin Riis said:**
> There is a python GTK client installed by default with Ubuntu.  

The best client for Unix is rtorrent, bar none.  It's available in the repositories.  

User Guide: 

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

just curious, what makes it so good? I have never, ever had it recommended before.

---

### Post by Quintin Riis on 2007-06-22
> **FleetAdmiral74 said:**
> just curious, what makes it so good? I have never, ever had it recommended before.
I have about 120kB/s up, 750kB/s down, as I write, and it's using a whole 3.5mB of core.  

It's fast, fast, FAST, doesn't take a lot of resources like some other clients do, and the controls are simple and beautiful.  Thanks to the ncurses interface, it works great with screen or detach.

---

### Post by Ssj3_man on 2007-06-22
> **FleetAdmiral74 said:**
> just curious, what makes it so good? I have never, ever had it recommended before.

ill try them all, but it all comes down to personal preference in the end. they all do the same thing right?

:)

---

### Post by Nigmah on 2007-06-22
[COLOR=DarkOrange]**as far as i can tell deluge doesn't have protocal encryption, so if your isp limits p2p you might want to get wine then install utorrent, it wont be perfect but its still better than nothing.**[/COLOR]

---

