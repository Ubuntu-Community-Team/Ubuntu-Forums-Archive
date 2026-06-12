---
title: "Anyone have a real solution for MULTIMEDIA PLUGINS for Firefox?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by quincyjones on 2006-05-08
Hey,
I'm running Breezy on a Dell Inspiron 1300. I feel I've tried everything to get all the multimedia working (specifically the firefox video plugins). I've tried following the multimedia apps wiki (incl restricted formats), Automatix, Easy Ubuntu (both off fresh installs), a script writen by "patrick295767", tried compiling mplayer from cvs, and others...

I really like Ubuntu but I also like being able to use the net properly!

I've had the best results with **mplayer** but in every case something still doesn't work *properly*, specifically: quicktime, windows media player, realplayer

What am I doing wrong?!! ](*,)

---

### Post by ZiLOG_Z80 on 2006-05-08
I've not really tried a lot of multimedia out but i have used the official real player and it worked well for real media

[http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer](http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer)

---

### Post by Omnios on 2006-05-08
Most people get the Media Player Connectivity extention from firefox. It works though it is not alway pretty.

---

### Post by quincyjones on 2006-05-08
Realplayer I can get to work relatively easily and well but quicktime and WMP, hardly at all. Surely this should be relatively easy, esp on a pretty standard system like mine with a fresh Breezy install?
](*,)

---

### Post by Bloch on 2006-05-08
To answer your question: No.
But on my apple mac I can't play the BBC clips, and they play fine on firefox with the mplayer plugin.
Hopefully someday soon web pages will settle on a few formats for multimedia. The mplayer plugin gets it right about 80% - 90% of the time.

---

### Post by quincyjones on 2006-05-08
**Omnios,** thanks -I'll try that

**Bloch,** How do you manage to get mplayer working 80% of the time! I'd be happy with that. What method do you use to install it?

---

### Post by nalmeth on 2006-05-08
hmm
my mplayer-plugin for firefox works 100%.
It never fails to play a video.
I will sometimes take a long time to play it, or play it a bit skippy, but I have no problems with it's performance.
I used automatix for breezy and bump's for dapper to install it

---

### Post by perce on 2006-05-08
I've installed realplayer, mplayer, and the mozilla plug-in for mplayer via apt-get from the universe and multiverse repositories. This works for many formats, but not for all. If you want to add support for more popular format like wmv you must install a package called w32codecs. You'll never find this package in the official repositories because it might be illegal. You find this package in an unofficial Debian repository manteined by Marillat. You can look for it in the website [www.apt-get.org](www.apt-get.org), download it and  installe it using dpkg. With that package installed you should have no more problems with multimedia.

---

### Post by user1397 on 2006-05-08
I use mplayer plugin and it has never failed me...so far

---

### Post by catlett on 2006-05-08
[QUOTE=quincyjones]Realplayer I can get to work relatively easily and well but quicktime and WMP, hardly at all. Surely this should be relatively easy, esp on a pretty standard system like mine with a fresh Breezy install?
](*,)[/QUOTE]
There is no Quicktime player or Windows Media Player for Linux. (unless I'm mistaken) You have to use an alternative media player that can play/and or convert those files for you. I get everything (at least it appears so) through mplayer and I got that through Automatix
Anyways here are the links to firefox/mozilla's plug ins. Look around for yourself.[https://pfs.mozilla.org/plugins/](https://pfs.mozilla.org/plugins/) and [http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html)

---

### Post by quincyjones on 2006-05-09
Hey, thanks for all your responses!
I should've mentioned that I'm pretty sure I've installed all the necessary codecs (free and non-free), win32, ffmpeg (libavcodec), and many others.
I've had mplayer working to the point where it *plays pretty much everything but Quicktime is jittery and Windows Media Player is seriously jumpy and jerky *(unwatchable). 

Could it be one of my hardware drivers? But then why do Realplayer, DVDs and others work fine?

---

### Post by nalmeth on 2006-05-09
I rarely have problems with wmv, but asf is always problematic. Arrg I hate asf!
Do you know how to change your video driver? 
Try changing the driver used by mplayer.
Go to the website, right-click on mplayer-plugin, and click configure
change the video driver
I have noticed this making a difference

---

### Post by quincyjones on 2006-05-09
I solved my problem, changed the drivers in mplayer config to sdl. 
So, incase anyone needs it, do: 
sudo gedit /etc/mplayer/mplayer.conf 
change "vo=x11" to "vo=sdl" and "ao=alsa" to "ao=sdl" 
(althogh my major problem seems to have been only with the audio driver!)
  :KS

_edit:_ I noticed now that it is suggested in the "restricted formats" wiki, under mplayer that you add the sdl driver option. I should've read more carefully...
After I also added/reinstalled every flash player (my last problem) item I could from the standard repositories and reinstalled the flash plugin, I now can't find a website that doesn't work perfecty! :)

---

