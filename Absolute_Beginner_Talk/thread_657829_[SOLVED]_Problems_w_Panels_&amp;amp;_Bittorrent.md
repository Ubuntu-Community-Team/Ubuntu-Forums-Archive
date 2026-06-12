---
title: "[SOLVED] Problems w/ Panels &amp;amp; Bittorrent"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-04
I'm running Xubuntu 7.10 on a Compaq Presario 5WV254 5000 Series with 256mb RAM and a 700Mhz AMD Duron Processoer. 

_**Bittorrent & Bittornado**_
   First off Ive installed and re-installed these programs several times with Synaptic Package Manager to no avail. I've scanned the details for errors in each package and there are none. Bittorrent doesn't show up in my applications after installation and when I run a search for it in Appfinder, it finds the program but when I try to execute the program I get prompted to 'Open location for Bittorent meta file', Bittornado doesn't show up in my applications either and Appfinder doesnt turn up any results at all.

**_Panels_**
   I figured out the panel problems through another thread.

---

### Post by Moop on 2008-01-04
Do you have Ubuntu installed or are you running it from the live cd? 

I don't think you can install applications when running from the live cd. 

Try Deluge for a bittorrent application. It's my favorite.

---

### Post by Semong on 2008-01-04
Xubuntu is fully installed on my machine.

---

### Post by jonnywombat on 2008-01-04
Not sure about xubuntu but in ubuntu bittorrent is installed by default..But it does not appear in the menus. To rectify this you can look in system>>preferences>>main menu.. and then look in internet and check bittorrent.. then it shows up.. 

Why bittornado is showing up tho I don't understand but to echo a previous comment I prefer deluge too.

Jonny

---

### Post by hyper_ch on 2008-01-04
bittorrent is a shell program (and I think bittornado also).

However I prefer running rtorrent as shell torrent client. Uses much less resources, is stable, works great, and controlable by a normal ssh connection ;)

---

### Post by uncannybuzzard on 2008-01-04
yeah, rtorrent is the way to go. look up a little program called 'screen'. it may be installed by default, if not do a ```
sudo apt-get install screen rtorrent
```
it can be a little daunting at first, but basically what screen does is allow you to run multiple terminals inside the same one (kinda like konsole tabs without the tabs). so what you do is run rtorrent in a screen and 'detach' it so that it runs on its own in the background.

---

### Post by hyper_ch on 2008-01-04
I agree, rTorrent and screen do magic together ;)

Anyway, here are some links to get you started:

This guide helped me getting hooked on rTorrent:
- [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

And those from the rTorrent homepage ([http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)) are also good to read:

- [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)
- [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)
- [http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)
(It's important that you create a .rtorrent.rc file that you use to start rTorrent with and that you set a session folder in there. Otherwise rTorrent will rehash all torrents upon each restart)

And for screen, this guide helped me to see the marvels of screen:

- [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by Semong on 2008-01-04
Thank you all for your suggestions. I've installed rtorrent . However I would still like to figure out why bittorent isnt working because a few other programs Ive installed arent showing up in my applications and I cant get them to run either.

---

### Post by Semong on 2008-01-12
bump

---

### Post by Semong on 2008-01-13
Even after a complete installation of Xubuntu 7.10 Gutsy on a freind of mine's computer Bittorent is no where to be found. I went into synaptic, reinstalled bittorrent, ran a search in app-finder, clicked bittorrent and once again I am prompted to 'Open Bittorrent Meta Files'. I figured this could be an error on my live cd however I checked it for errors once again and there are none. What could I possibly do to fix this?

---

### Post by RomeReactor on 2008-01-13
> **Semong said:**
> ... clicked bittorrent and once again I am prompted to 'Open Bittorrent Meta Files'...

Hi. This is the default behavior of Gnome's BitTorrent client. It doesn't show up in the menus since the GUI only handles one download. You start the GUI by double-clicking a **.torrent** file, which will result in the GUI showing up asking you where to save the download. If you enabled the menu entry, then launching it from there will result in the **Open Bittorrent Meta Files** dialog showing up: it's asking you for the .torrent file to start the download. If you close the program before the download is completed, you can resume the download by double-clicking the same .torrent file again, and this time it will ask you if you want to resume. To launch the GUI from the terminal:
```
gnome-btdownload
```
This will open the **Open Bittorrent Meta Files** dialog.

If you want to use BitTorrent from the terminal to download a single file:
```
btdownloadcurses /PATH/TO/FILE.torrent
```

If you want to download many simultaneous torrents:
```
btlaunchmanycurses /PATH/TO/DIRECTORY
```
In this case, DIRECTORY is the folder where the .torrent files are stored. You can delete indivudual .torrent files when you finish the download or don't want to seed this file anymore; you can also add files to the folder and they'll start to download automatically.

Personally, I find **btlaunchmanycurses** to be a very good way to download torrents.

---

### Post by Semong on 2008-01-13
Ahh thank you, my friend. If I had read up on Bittorent a little more perhaps I would've figured that out on my own but I was expecting Bittorent to be like Limewire for windows oddly enough. Once again thank you.

---

