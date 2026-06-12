---
title: "Getting MPlayer"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-18
hey guys

Could somebody teach me how to install and get the MPLayer for my Ubuntu LTS version 6 , and what are the good movie editing softwares that i can use to ?:rolleyes: 

and also having a hard time installing wine and using it. I have no idea how to get it to work.do i have to click on some icon or something after installiation ...?? #-o 

your help will be much apperciated. =D>

---

### Post by voodoonirvana on 2006-09-18
> **lifemaximum said:**
> hey guys

Could somebody teach me how to install and get the MPLayer for my Ubuntu LTS version 6 , and what are the good movie editing softwares that i can use to ?:rolleyes: 

and also having a hard time installing wine and using it. I have no idea how to get it to work.do i have to click on some icon or something after installiation ...?? #-o 

your help will be much apperciated. =D>

Im in teh same situation, well with the video editing part that is. I forgot how I installed MPlayer, search MPlayer in these forums. Ive been trying to get LiVES video editor installed for the longest time now. There is one that comes in the add/remove programs called Kino but it only uses raw DV and avi formats so it sucks.

---

### Post by Marsolin on 2006-09-18
You should be able to install [MPlayer]("http://linuxappfinder.com/package/mplayer") directly from the Ubuntu repositories. If you aren't seeing it, you might need to enable the universe repository. You can do that through Synaptic.

Some good video editors that are in the Ubuntu repositories are [Avidemux]("http://linuxappfinder.com/package/avidemux"), [PiTiVi]("http://linuxappfinder.com/package/pitivi"), and [Kino]("http://linuxappfinder.com/package/kino").

[Cinelerra]("http://linuxappfinder.com/package/cinelerra"), [Jahshaka]("http://linuxappfinder.com/package/jahshaka"), [LiVES]("http://linuxappfinder.com/package/lives"), and [KDEnlive]("http://linuxappfinder.com/package/kdenlive") are available in deb format through other repositories.

If you want to branch beyond those then you can try [OpenMovieEditor]("http://linuxappfinder.com/package/openmovieeditor"), but I suggest one of the others.

Another cool editor is called [eyespot]("http://linuxappfinder.com/package/eyespot"). It runs through a web browser and is geared for creating videos to share online.

---

### Post by CarpKing on 2006-09-18
Wine is a commandline program, so to use it you open a terminal and cd to the directory where your .exe file is (we'll call it example.exe), then type
```
wine example.exe
```

EDIT:
After installing Wine, you need to open up a terminal and type 
```
winecfg
```

This will set up the Wine directory structure, and you can later use this command for any configuring you need to do.  

In Nautilus, the file browser, you should also be able to just double click on the .exe file, or right click-> Open with Wine.

---

### Post by lifemaximum on 2006-09-19
Cool thanks everyone.... will try that....:cool:

---

### Post by lifemaximum on 2006-09-20
hey

i tried the winecfg code that u said... the configuration window opened and when i was reading through the setting and making adjustement it went off and than i saw this msg in the terminal
[I][COLOR="Red"]
faz@faz-laptop:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Creating link /home/faz/.kde/socket-faz-laptop.
can't create mcop directory
[/COLOR][/I]

so what should i do now ?  


and one more thing i got the package for [COLOR="Red"]**_cinelerra_2.0.0-1svn20060611.1_i386.deb_**[/COLOR] the movie editor i believe, i got the debian package and used the debain package installer to install it ...

but i got a error msg saying [COLOR="Blue"]Error Dependancy is not satisfiable[/COLOR]...so any suggestions???

---

### Post by Najand on 2006-09-20
```

sudo aptitude install mplayer mozilla-mplayer mplayer-fonts

```

---

### Post by windquest on 2006-09-20
For MPlayer and a host of other programs,help and configuration, I found the site
 [http://ubuntuguide.org/wiki/Dapper#General_Notes](http://ubuntuguide.org/wiki/Dapper#General_Notes)

to be wonderful help for a beginner.
Henry

---

