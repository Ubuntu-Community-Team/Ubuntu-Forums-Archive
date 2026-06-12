---
title: "Asolute Newbie / i want this software help"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by 010100 on 2007-07-15
Hello im newbie i want to someone help me to search the next long list of software that i want to use on Ubuntu
well this its the long list :oops:
--Zip/rar Tools and file joiners---
Rar
7zip
kamaleon 2
Hacha
--Media Players, codecs and editors--
Quick time and Itunes ( i really love iTunes)
K-lite codec pack
Avisynth
Virtual Dub Mod
tmpg enc
Sony Vegas or another good video editor
DVD decryter or img burning
Power DVD  Blu-ray-HD_DVD edition
AC3 DEcoder
KMplayer
VLC player
x264 / megui / Mkv toolkit
rat DVD
Real Player
--Burning / back up stuff--
Nero
Roxio
Img burning
Alcohol 120
--Web browsers--
Fire Fox i know that linux have this
Opera
--Leech tools--
Sysreset ( i want this bcuz im a Irc server and i love this damn good scrip i got a hope)
FlashGet ( also a damn good dowload manager that i will like to keep)
Peer to mail  P2P/P2M
Pando P2P
Ares P2P
uTorrent
--Misc tools--
MSn messenger
Aegisub  (For subtitles edition)
Photo shop CS2*CS3
Foxit PDF 
Google Earth
--Games--
I want emulators of console systems


----------
Well thats all i hope that some kind person help me whit that 
Tnkx for take time to read this
:oops: :)  :D

---

### Post by oilchangeguy on 2007-07-15
read this:
[http://www.linuxeq.com/](http://www.linuxeq.com/)
some of the info may be outdated. but you'll still get a good idea about what's out there.

---

### Post by Skidpad on 2007-07-15
Or this: [LinuxAppFinder]("http://linuxappfinder.com/windows")

---

### Post by techno-mole on 2007-07-15
from what i can gather alot of what you want to run is for windows only, for example i dont think there is a k-lite codec pack for linux, this is the case with alot of the stuff in your list, so you will have to find alternatives that run under linux, and for anything that you cant find an alternative for you can try running it over wine.
wine is an application that adds a compatibility layer to linux enabling windows applications to run.
as for things like codecs again for example you will need different ones, which are in the repo's and there are various guides about getting and installing them.
there are some very good alternatives to things like dvd decrypter and such like, try looking into k3b, k9copy, xdvdshrink, and there are more, again they can be downloaded from the repo's.
cheers

---

### Post by Outrunner on 2007-07-15
> **techno-mole said:**
> from what i can gather alot of what you want to run is for windows only, for example i dont think there is a k-lite codec pack for linux,

Nope, but there's this command xD

```
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs
```

Side note, I love your username, its really cool :)

---

### Post by alex_anthony on 2007-07-15
--Zip/rar Tools and file joiners---
Rar  --[COLOR="Red"]needs rar package[/COLOR]
7zip -- [COLOR="Red"]built in archive manager/7zip easy to install[/COLOR]
kamaleon 2 [COLOR="Red"]build in archive manager/ others in repos[/COLOR]
Hacha - [COLOR="Red"]as above[/COLOR]
--Media Players, codecs and editors--
Quick time and Itunes ( i really love iTunes)  --[COLOR="Red"]Various itunes replacements - I like exaile, also banshee, amarok, etc[/COLOR]
K-lite codec pack -- [COLOR="Red"]codecs can be downloaded from repos (or automatix)[/COLOR]
Avisynth [COLOR="Red"]kino/ cinelerra/ others (??)[/COLOR]
Virtual Dub Mod [COLOR="Red"]as above[/COLOR]
tmpg enc [COLOR="Red"]ffmpeg (and front end??????[/COLOR]
Sony Vegas or another good video editor --[COLOR="Red"]kino/cinelerra(?) and many others[/COLOR]
DVD decryter or img burning --[COLOR="Red"]decrypting - Acid rip[/COLOR]
Power DVD Blu-ray-HD_DVD edition -- [COLOR="Red"]I saw something about bluray&hddvd. pretty much install something to make readable and then use any player[/COLOR]
AC3 DEcoder [COLOR="Red"]Sound converter perhaps[/COLOR]
KMplayer -- [COLOR="Red"]VLC (below) to play, built in screenshot/ istanbul screen capture (may need other converter)[/COLOR]
VLC player -- [COLOR="Red"]available, in repos[/COLOR]
x264 / megui / Mkv toolkit
rat DVD -- [COLOR="Red"]doubt it, you'll have to have bigger files from e.g Acid Rip[/COLOR]
Real Player 
--Burning / back up stuff--
Nero -- [COLOR="Red"]gnomebaker/k3b and others[/COLOR]
Roxio -- [COLOR="Red"]gnomebaker/k3b and others[/COLOR]
Img burning [COLOR="Red"]Default Nautilus CD Maker can burn ISO, also gnomebaker, k3b, others[/COLOR]
Alcohol 120 [COLOR="Red"]iso can be mounted by command line, or frontend gmount/gmountiso[/COLOR]
--Web browsers--
Fire Fox i know that linux have this [COLOR="Red"]correct, installed by default[/COLOR]
Opera - [COLOR="Red"]in reposI think[/COLOR]
--Leech tools--
Sysreset ( i want this bcuz im a Irc server and i love this damn good scrip i got a hope) [COLOR="Red"] unsure, doubt if works under wine[/COLOR]
FlashGet ( also a damn good dowload manager that i will like to keep) -- [COLOR="Red"]gwget, new program celerius is in development, not available yet tho[/COLOR]
Peer to mail P2P/P2M [COLOR="Red"]apparently runs almost perfectly under wine [_see here_]("http://appdb.winehq.org/appview.php?iVersionId=4188")[/COLOR]
Pando P2P [COLOR="Red"]no (may run under wine)<--- now I doubt this.[/COLOR]
Ares P2P -- [COLOR="Red"]should work under wine [_see here_]("http://appdb.winehq.org/appview.php?iVersionId=7678")[/COLOR]
uTorrent - [COLOR="Red"]works under wine (windows compatibility layer), alternatives available - azureus, deluge, ktorrent[/COLOR]
--Misc tools--
MSn messenger - [COLOR="Red"]GAIM (now pidgin) installed by default, aMSN in repos[/COLOR]
Aegisub (For subtitles edition) [COLOR="Red"]new linux version available...          for others -  various e.g. subtitleeditor. search repos[/COLOR]
Photo shop CS2*CS3 [COLOR="Red"]GIMP installed by default[/COLOR]
Foxit PDF [COLOR="Red"]Document Viewer installed by default reads pdf[/COLOR]
Google Earth [COLOR="Red"]Available, not sure if in standard repos[/COLOR]
--Games--
I want emulators of console systems -- [COLOR="Red"]PS1 available - search repos[/COLOR]

---

### Post by Nythain on 2007-07-15
> 
Rar
7zip

available in the ubuntu repositories
> 
kamaleon 2
Hacha

not familiar with these programs so i dont know
> 
Quick time and Itunes ( i really love iTunes)

itunes in linux is a REAL pain... not easily accomplished by the novice user
> 
K-lite codec pack

possibly w32codecs package in the medibuntu repositories
> 
Avisynth
Virtual Dub Mod
tmpg enc
Sony Vegas or another good video editor
DVD decryter or img burning
Power DVD  Blu-ray-HD_DVD edition
AC3 DEcoder

ffmpeg, avidemux (or however its spelled), devede, and countless others
> 
KMplayer
VLC player

both are available in the ubuntu repos i believe
> 
x264 / megui / Mkv toolkit
rat DVD
Real Player

cant help you on these, never used them
> 
Nero
Roxio
Img burning
Alcohol 120

K3B, nero linux, and the cli command mount
> 
Fire Fox i know that linux have this
Opera

both available in the repos... think opera needs you to enable the canonical repository
> 
uTorrent

you can either use the amazing KTorrent, rTorrent, or wine uTorrent if you MUST
> 
MSn messenger

TONS of instant messager clients available, i preferred Kopete
> 
Photo shop CS2*CS3

you might want to consider dual booting for that one, or if your machine can handle it, running windows virtually via VMWare or VirtualBox... The Gimp is a close equivalent, but it is NO Photoshop
> 
Foxit PDF

not sure if thats a pdf viewer or firefox plugin for one... acroread and the acroread mozilla plugin are pretty effective
> 
Google Earth

forget wich repo this is in, but i think its medibuntu
> 
I want emulators of console systems

all the popular emulators have linux ports... visualboy advance is cli, but there are front ends for it... zsnes is exactly the same... gens for genesis... theres a port of epsxe for linux available on the net

---

