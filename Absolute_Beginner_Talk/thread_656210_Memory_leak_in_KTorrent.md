---
title: "Memory leak in KTorrent?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-02
I just installed a system monitor (conky) and noticed just how much of a resource hog Ktorrent is. At the moment it is using 40% (175mb) of my RAM. Granted there are 3 torrents being downloaded at the same time (though I am not connected to many peers), but surely there is something wrong? My first guess was a memory leak, but I am not much of an expert.

---

### Post by fs3rp4 on 2008-01-02
This is commom in P2P programs. Otherwise the access disk will be increased a lot.

---

### Post by intense.ego on 2008-01-02
Is there any way to correct it because I know that these issues do not have to occur. For example, with utorrent on windows, hardly any system resources need to be used.

---

### Post by fs3rp4 on 2008-01-02
Try setting memory usage to "low" under Advanced in the configuration dialog...

---

### Post by Ub1476 on 2008-01-02
[Deluge]("http://deluge-torrent.org/") uses about 50mb on my comp. Ktorrent is written for KDE too, so that might slow it down.

---

### Post by Dark Hornet on 2008-01-02
I (tried) to use Ktorrent on my Ubuntu set up--its a great program, however without fail, it would crash my entire system to where I would have to do a hard boot.  I switched over to Deluge, and it is so much better for the Gnome OS IMO.  So personally, I would recommend that....have fun.

---

### Post by intense.ego on 2008-01-02
I'll try setting the memory usage to low. If that doesn't improve the situation I'll switch over to Deluge. The reason I am so reluctant to switch right now is that I have a number of large files downloading and I am too lazy to migrate them to Deluge and to get accustomed to a new application.

---

### Post by intense.ego on 2008-01-02
It has been a while and the situation seems to have improved. It is now running at 20% RAM (about 80mb). Should I install Deluge? If so, how do I know which of these packages to use ([http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)). I am using Feisty Fawn. I plan on installing Deluge and comparing its features to Ktorrent before completely switching over.

---

### Post by intense.ego on 2008-01-03
bump, anyone?


EDIT: oops, sorry. I accidentally marked this thread as solved.

---

### Post by hyper_ch on 2008-01-03
if you want a lightweight-torrent client, use rtorrent. It's in the repos.
It is completel shell controlled - doesn't have a gui.

If you want a nice beginner howto, let me know.

---

### Post by intense.ego on 2008-01-03
I've heard about rTorrent and it sounds really good but I need a GUI. Does anyone know which Deluge installation file corresponds to what systems?

---

### Post by hyper_ch on 2008-01-03
why do you need a gui?

rTorrent is quite simple to use ;)

---

### Post by Sukarn on 2008-01-04
> **hyper_ch said:**
> why do you need a gui?

rTorrent is quite simple to use ;)

For one, I have a torrent that rtorrent fails to open and crashes when trying to open it.

Its running fine in Deluge though.

I can't really share the torrent on a public site, if you know what I mean, so sorry, I can't give out this torrent as an example.

I don't know if it matters or not, but the torrent has about 4.3 GB of data in various avi files.

---

### Post by hyper_ch on 2008-01-04
I have a 54 GB torrent with multiple .mkv/.mp3/.ogg files ;)

If rTorrent doesn't like that one, the the torrent is fishy...

---

### Post by Sukarn on 2008-01-04
> **hyper_ch said:**
> I have a 54 GB torrent with multiple .mkv/.mp3/.ogg files ;)

If rTorrent doesn't like that one, the the torrent is fishy...

Actually, it turned out that my copy of rtorrent was bad. I purged my self-compiled rtorrent and installed the one from Gutsy repos, and its working fine with the above mentioned torrent. I miss the dht and peer exchange from the newer one though.

---

### Post by hyper_ch on 2008-01-04
well, the current commit has a bug which can easily be fixed (makes it only compile on bsd)... not sure if rakshasa already did upgrade the version in SVN...

---

