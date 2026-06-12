---
title: "BitTorrent in Fluxbuntu 7.10"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by joeyt2k on 2008-01-26
I apt-get installed bittorrent on a fluxbuntu 7.10 laptop. 

In Firefox I click on a torrent, and select save.

I get a "yield sign" with the torrent name in my home folder. 

I assign btdownloadcurses as the run action. I run it, nothing happens.

I've also tried selecting "open with" instead of "save" after clicking on the torrent link, and using btdownloadcurses. Same result.

Also tried bittornado, same result.

Any help is appreciated.

---

### Post by UltraMathMan on 2008-01-26
Personally I like Azureus [http://azureus.sourceforge.net/]("http://azureus.sourceforge.net/") 
```
sudo apt-get install azureus
```

For a command-line based approach screen and rtorrent is the way to go.

-Hope this helps :)

---

### Post by RomeReactor on 2008-01-26
Hi. Btdownloadcurses is a command line program; once you download the .torrent file, open a terminal , navigagate to where you want to save the download, then run:
```
btdownloadcurses /PATH/TO/FILE
```
where FILE is the .torrent file you downloaded. You can also download [many simultaneous files]("http://ubuntuforums.org/showpost.php?p=4203019&postcount=27") using BitTorrent from the terminal.

You can get a graphical interface for it:
```
sudo aptitude install gnome-btdownload
```
or:
```
sudo aptitude install bittorrent-gui
```

---

### Post by joeyt2k on 2008-01-26
Thank you very much.

---

