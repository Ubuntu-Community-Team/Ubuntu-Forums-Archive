---
title: "mplayer shuffle"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-12-29
Is it possible to use


mplayer ./*

to play all the songs in a folder

but also have the songs play randomly with some option?

thanks

i.e. something like

mplayer ./* --shuffle

---

### Post by blueridgedog on 2007-12-30
the command:

man mplayer

Implies that the sytax woudl be -shuffle

So try:

mplayer ./* -shuffle

---

### Post by vinnybad on 2008-02-09
Hey ssaamon,

I don't know about you but I have my music sorted in artist -> albumName -> songName.mp3 where there are many artists with perhaps more than 1 album with more than 1 song.  Anyway, when I want to listen to all of the songs in shuffle mode, things get a little tougher...but not so tough!

I go to my music folder.

find ./ -name "*.mp3" -print > playlist.txt
mplayer -playlist playlist.txt -shuffle

The first line finds all files with ending .mp3 and redirects output to the file playlist.txt

The second line calls mplayer with a playlist with the shuffle option...

pretty cool!

---

