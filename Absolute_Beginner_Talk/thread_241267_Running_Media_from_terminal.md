---
title: "Running Media from terminal"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-22
Hey, i know how to run programs from terminal, but what about media? Movies, pics, ect

---

### Post by Brownedwg89 on 2006-08-22
program you want to use followed by the media you want to play

for example:
```
vlc movie.avi
juk song.mp3
```

---

### Post by kwalo on 2006-08-22
You don't need X to watch movies. Try:```
mplayer -vo aa some.movie
``` Of course you can watch movies in mplayer, the normal way. Just skip the -vo aa options.

Music can be played with [xmms2](http://wiki.xmms2.xmms.se/index.php/Main_Page). There is a .deb package for dapper. Launch it with:```
xmms2-launcher
```Then type:```
xmms2
xmms2 mlib
``` to see what options this program has. Use```
xmms2 radd some/directory
```To add all music files found in some/directory. Install some [other clients](http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients), which run with xmms2.

---

### Post by mcduck on 2006-08-22
For music, there are far better options than xmms2. 'play'-command works by default, so you can just run 'play ~/music/*.mp3' or 'play mymusic.mp3' or whatever. And then there's MPD, that offers very fast and flexible music player with library, usable with both GUI and CLI clients. NCMPC is a great text client for MPD.

oh, as well as -aa, you can watch movies in text-mode with colors with -caca. Looks a bit nasty with movies, but cartoons and such work fine.

I don't know any image viewing app for terminal, but Imagemagick sure is a great CLI tool for editing images.

---

### Post by kwalo on 2006-08-22
> **mcduck said:**
> For music, there are far better options than xmms2. (...) And then there's MPD, that offers very fast and flexible music player with library, usable with both GUI and CLI clients. NCMPC is a great text client for MPD.
Xmms2 is a fresh project, but it does provide many GUI clients as well. Have you checked [http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients](http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients)
For less sophisticated console music players there are:
mpg123 - For mp3's - it's in multiverse
mpg321 - Same as above, only free (universe repository)
ogg123 - Plays ogg files
aplay - Like play, using alsa
moc - (Music On Console) - this music player uses ncurses library.

---

