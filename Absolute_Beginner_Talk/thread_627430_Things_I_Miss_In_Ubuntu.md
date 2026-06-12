---
title: "Things I Miss In Ubuntu"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by antalk on 2007-11-30
I'm trying to switch to Ubuntu from MS Windows XP. It's a nice op system and I really like the available softwares, but there are some things I really miss.. I wonder if you can help me to find some Linux alternatives:

- Video editor software. I do not need a professional one, but something on the level of Windows Movie Maker. I have a DV cam with a USB cable. I tried Kino, but there are some problems.
* It's impossible to connect the cam with USB, so I'd need a firewire cable and a card.
* I imported my videos in wmv, avi and mpeg, but Kino was unable to open them.

- Hardware control panel. It'd be nice to see all my hardware stuffs on a single page.

- I have a Samsung SyncMaster 793mb monitor. I was unable to set up the screen resolution correctly. I used in 1024x768 @ 75Hz under Windows and it works with this settings with Ubuntu, too. However the menus, panels and other GUI stuffs are much more rustic in Ubuntu. (The characters are larger and there are big empty spaces around them.) When I swicth to a bigger screen resolution it runs on 70Hz or even 55Hz... that really hurts my eyes. And I even noticed that sometimes the whole displayed screen begings shaking very slightly, so the characters look fuzzy. (No hardware failure, it works properly with Windows.)

- I installed firestarter to filter IMCP answers from my system. It seems runnning, but I always see a red "failed" error sign on the boot up screen.

- Moreover it's not an Ubuntu problem, I guess, but I mention it... some streaming media files do not start on various webpages ( e.g. street webcams at [http://www.utv.hu](http://www.utv.hu) ). Even there are embedded flash videos that work under windows, but they do not start under Ubuntu/Firefox/non-free flash plugin. (e.g. [http://www.juj.hu](http://www.juj.hu) )

---

### Post by twistedtwig on 2007-11-30
which version of Ubuntu do you have installed?

have a look at this magazine online... it has an article about video editing for Linux

[http://fullcirclemagazine.org/2007/11/29/issue-7-released/](http://fullcirclemagazine.org/2007/11/29/issue-7-released/)

GL

---

### Post by Gone fishing on 2007-11-30
For the video playback you will need the codec these can be got from medibuntu medibuntu.org. Personally I use gxine and mplayer as media players they seem to work great and I can pan and scan etc I think you need to add universe to your repository list.

My DivX and Xvid  playback in Ubuntu is better than Windows.

---

### Post by sourcemorph on 2007-11-30
u can use avidemux... its kinda cool, i think u can do almost everything that u do in movie maker.

and yeah u can edit the xorg.conf file in /etc/X11... add the resolution u want, its quite easy but do make a backup of the file before editing it.which ubuntu do u use btw... 7.10 has a pretty good support for various monitors n graphics cards.

---

### Post by ofir_k on 2007-11-30
A good video editor: kdenlive
(remember to switch off desktop effects while working with it, because it makes problems otherwise)

Install sysinfo from "Add/Remove...". Then it will appear in "System Tools" in the apps menu

For streaming, install vlc (a great video player!), and the firefox extension "MediaPlayerConnectivity".

---

