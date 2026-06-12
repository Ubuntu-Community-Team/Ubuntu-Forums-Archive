---
title: "Exaile:The best Media player![Gnome]"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-14
[IMG]http://www.imgx.org/pfiles/1382/exaile-logo.jpg[/IMG]Exaile is a music player aiming to be similar to KDE's Amarok, but for GTK+ and written in Python. It incorporates many of the cool things from Amarok (and other media players) like automatic fetching of album art, handling of large libraries, lyrics fetching, artist/album information via Wikipedia, Last.fm submission support, and optional iPod support via a plugin.

In addition, Exaile also includes a built-in SHOUTcast directory browser, tabbed playlists (so you can have more than one playlist open at a time), blacklisting of tracks (so they don't get scanned into your library), downloading of guitar tablature from fretplay.com, and submitting played tracks on your iPod to Last.fm.

[CENTER][[IMG]http://www.imgx.org/pthumbs/large/1381/exaile_large.jpg[/IMG]]("http://www.imgx.org/public/view/full/1381")[/CENTER]

**Exaile 0.2.10**

[LIST]
[*] Plugin Manager improvements &#8211; you can now install plugins from within the plugin manager
[*] Scriptable Radio Panel &#8211; People will be able to write plugins for your favorite streaming service. (currently shoutcast is available)
[*] Lots of new translations
[*] New music sharing plugin &#8211; you can share your music with people using iTunes or other people using Exaile

See whole Changelog  - [ChangeLog - Exaile - Trac](http://www.exaile.org/trac/wiki/ChangeLog)

Installation : - 2 Installation methods as usual :)

[LIST]
[*]Open Terminal and type this :- 
[/LIST]
```
sudo apt-get install exaile
```
[LIST]
[*]2 Installation Step
[/LIST]
Open Terminal and type following : -

```
sudo gedit /etc/apt/sources.list
```

Add these lines at the bottom and save 

```
deb http://download.tuxfamily.org/syzygy42 feisty exaile
```

and then type the following in terminal : make sure you have saved above step ;)
```

wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg
sudo apt-key add 8434D43A.gpg
sudo apt-get update
sudo apt-get install exaile
```

For Fedora users : - 

```
yum install exaile
```

Enjoyy the best player for Gnome :hap2: 

[CENTER][[IMG]http://www.imgx.org/pthumbs/large/1383/rating_large.png[/IMG]]("http://www.imgx.org/public/view/full/1383")[/CENTER]

Home Page : [Exaile | Music Player for GTK+](http://www.exaile.org/)
Plugins  : [Exaile | Music Player for GTK+: Plugin List](http://www.exaile.org/plugs)

---

