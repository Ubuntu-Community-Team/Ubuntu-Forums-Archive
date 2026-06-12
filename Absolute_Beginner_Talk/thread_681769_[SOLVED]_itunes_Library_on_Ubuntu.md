---
title: "[SOLVED] itunes Library on Ubuntu"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by firestormx37 on 2008-01-29
On Ubuntu, I use Banshee to organize and play all of my music.  However, I want to use itunes to manage my ipod.  So I got itunes running using wine and I have copied my library files into the itunes directory on wine.  Now what I need to know is how do I reference my music files from inside wine.  I have my music stored on a partition that is mounted in /media/sda2.  What I want to do is just go through the library file with a find/replace so that all the paths are correct.  Currently each of the entries references the music as I had it in windows:

file://localhost/D:/Music/........

I want each of them to reference /media/sda2/Music.

What is the correct syntax?

Is it file://media/sda2/Music.....?

I have been playing around with it, but I am unable to get it to work.  Any help / suggestions would be appreciated. Thanks.

---

### Post by firestormx37 on 2008-01-29
I may have figured this one out myself.  I realized that wine has the Z drive mapped to /.  I fixed it, and it seems to be importing the files now, we'll see if it works.

---

### Post by tgalati4 on 2008-01-29
What processor do you have and how is the performance of iTunes under wine?

---

### Post by firestormx37 on 2008-01-29
I have an Intel Core Duo 2.0 GHZ (T2500).  Itunes is a little sluggish with wine, but considering the size of my music library (over 40 GB), it handles it pretty well.  The lag mostly seems to be when switching between large playlists or to my entire music library.  Banshee performs the same way with my library.  I have not tested the ipod with it yet, so I am not sure how that will work.  Otherwise, itunes works fine.

For anyone looking for the solution to my problem:

I had a drive (z:\ ) defined in wine as my root directory.  I then copied my itunes library (the xml file) from windows.  Open the xml file in a text editor and then do a find/ replace.  When finished, my song locations were in the format of "file://localhost/z:/media/sda2/Music....."

---

### Post by Linkz57 on 2008-01-29
Songbird works well for me, and there are many plugins (like directly importing your itunes xml library, and ipod support)
[http://www.songbirdnest.com/](http://www.songbirdnest.com/)
seems easer then going through wine

as far as wine goes, i have no idea...

---

