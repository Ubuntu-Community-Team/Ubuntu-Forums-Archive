---
title: "DVD-playback-problems on Intrepid with fglrx on my iMac"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by moviemaniac on 2008-11-04
Hi guys,

I just wanted to inquire whether anyone else has this problem:

I need the fglrx-drivers for hardware-acceleration (Radeon HD2600 XT) so I installed those, Compiz is disabled.

Being an avid DVD-collector, movie-critic and DVD-reviewer (nearly 700DVDs in my collection...) I obviously want/need to watch DVDs on my machine and need AC3/DTS-passthrough as well as closed captions-support, so these are my choices and problems:

- Xine has been my preferred DVD-playback-program on previous Ubuntu-versions and on other machines. However, on Intrepid and with the fglrx-drivers it is currently unusable. The video-output is completely unidentifiable, it looks like there are virtually hundreds of horizontal tearing-lines. I've been through all the settings, but only the opengl-setting produces watchable output, all others fail. But OpenGL is unusable, too, due to dropped frames and the resulting tearing. 
- VLC works with X11 but it has crappy deinterlacing filters, so I don't want to use it/can't use it when reviewing DVDs. No support for closed captions either.
- Mplayer should work, but there's no easy way to get it to passthrough AC3 and DTS-streams and to switch that setting on and off as desired. I don't like the way of navigating with that software, too. I also don't think it supports closed captions.
- Kaffeine works (even though it uses Xine-libs) but there is no small chance that enabling/disabling the deinterlacing filters hardlocks my system. Very annoing.
- Ogle, well, there seems to be a bug that doesn't allow me to bring up the preferences-dialogue...

My main focus for 2 days was to get Xine to work. I installed uninstalled and reinstalled the fglrx-driver provided in the repositories, I triedd to install it from Ati.com (which, obviously, didn't work due to the lack of support for the new X-server), I changed the options in Xorg.conf, tried every possible combination of settings in Xine, read hundreds of pages, howtos and possible bug reports - it just doesn't want to work, end of story.

My only option to watch DVDs hassle-free right now is to use the DVD-Player on OSX which works really well. But, well, I'd prefer it if I didn't have to (re-)boot into OSX just to watch a DVD...

Does anyone here have similar problems with DVD-playback? (Just in case anyone asks: Yes, all the codecs and - ahem - required libraries are installed). If anyone knows a fix to get Xine to work - please come forward, but the main purpose of this thread is to see whether I'm the only one with these problems or not :lolflag:

---

### Post by cyberdork33 on 2008-11-04
although I haven't heard anything recently, this wouldn't be the first time there was a problem with ATI and video. Ubuntu happens to have these special versions of fglrx from ATI that works with xserver 1.5...
[http://www.phoronix.com/scan.php?page=news_item&px=Njc4OA](http://www.phoronix.com/scan.php?page=news_item&px=Njc4OA)

I'd guess it is a bug in the driver.

---

### Post by moviemaniac on 2008-11-04
That's my guess, too, I tested and retested every other possibility. But, you know, the funny thing is that Xine doesn't work but Kaffeine does when they both rely on the same libraries, that's something that doesn't want to get out of my head. 
Personally, I'm down to two options:
a) bug in the driver (maybe concerning Apples special version of the video card or otherwise we'd have heard about this before if it were a general bug) so I'll have to drink tea waiting for a fix
b) a problem/bug in Xine-UI (due to Kaffeine working with the same core-libs)

Just in case anyone wants to see what the video-output in Xine looks like:
[ATTACH]91142[/ATTACH]

---

