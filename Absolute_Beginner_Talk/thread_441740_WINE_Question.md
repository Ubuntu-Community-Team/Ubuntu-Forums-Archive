---
title: "WINE Question"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Fallen2 on 2007-05-12
Is it possible to run Windows Media Player and Windows Live Messenger using WINE?

---

### Post by starcraft.man on 2007-05-12
Why would you want Windows media player? Ubuntu has **Totem** / VLC / Mplayer for movies, and **Banshee** / Rhythmbox / Amarok / Exaile / XMMS for media... my main players are bolded, I like those :)

Honestly though, the whole point of installing Ubuntu is to get away from MS products... and no to my knowledge you can't just run WMP in WINE, its part of the core of XP/Vista. 

As for Windows Live Messenger. Install aMSN... type the bellow into a terminal (Applications > Accessories > Terminal)

```
sudo aptitude install amsn
```

aMSN has almost all of Lives features.

If you absolutely must have those two apps though and you don't want to try Ubuntu's players/aMSN, maybe windows is what you want... up to you.

Note: To install any of the players (totem and rhythmbox already installed) just substitute any of them for amsn in the above code (for isntance, vlc, mplayer, amarok).

Oh and I do not believe live messenger has worked properly under wine either...

---

### Post by Fallen2 on 2007-05-12
Thanks.  But how do I use WINE now that I have it installed.  Im new to all this Linux stuff and I want to learn.

---

### Post by starcraft.man on 2007-05-12
> **Fallen2 said:**
> Thanks.  But how do I use WINE now that I have it installed.  Im new to all this Linux stuff and I want to learn.

WINE is easy to use, if it works with your program its usually listed [here.]("http://appdb.winehq.org/") thats the appDB, most programs tested are there. The testers usually also make notes about certain glitches/fixes for programs.

The generic way to start a program in wine is to do this in Terminal:

```
wine /path/to/file
```

where path/to/file is replaced by wherever the setup EXE is, use absolute paths it will make sure ya never have a mistake.

That said, I do advise ya to look at all the [linux alternatives]("http://linuxappfinder.com/windows") to windows programs in this list and on [linux app finder]("http://linuxappfinder.com/") by category on left. You should be able to find a suitable program, if its something popular.

Oh and, if your having trouble with movies/audio cuz of codecs, do check [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") out pls. As well as Ubuntuguide.org itself in my sig, the index has answers to lots of common quetions.

*SALUTE* Welcome to the Ubuntu Army recruit, now get on with your training :p

Hehe, hope thats all your questions, have fun :D

---

### Post by jonward0690 on 2007-05-12
You can not run windows media player because they require you to verify your copy of Windows so the verification would fail anyways.

---

### Post by LollYouSuckZor on 2007-05-12
wine /path/to/file

I am installing BF2 right now :)! The path was something like...

/media/cdrom0/setup.exe


Because it was on a CD.

When you download it, open the folder, at the top there should be something that looks similar to, /media/cdrom0, desktop perhaps.  That what you would have after the wine, it'l start installing after then. :)

---

