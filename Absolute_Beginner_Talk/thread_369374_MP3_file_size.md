---
title: "MP3 file size?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Heedbanger on 2007-02-24
Hi I am new to using linux  and am hoping someone can help me with this problem.


I have just read a how to on ripping a CD into MP3 format using sound juicer,  I was able to get this working ok and ripped the CD no problem but when i looked at properties the file size for 1 song was 42mb.

Below is the line i entered into the gstreamer pipline in properties.
 audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=128 ! id3v2mux

How do I rip a cd into MP3 at a much lower file size (also i need the bitrate to be 128 to play on an mp3 player i have in my car).  

I have a lot of CD's to rip and they would take up far to much space on the hard drive at this size per song, in windows using creative player to rip CD's into MP3 the songs are usually  only about 4 - 5 mb each.

Can anyone point me in the direction of a better way to rip MP3 (at 128 bitrate) and have the low file size I usually have on my MP3 files in windows.

Thanks

---

### Post by equal on 2007-02-24
It looks like it's not working properly. That happens sometimes. Try this. In the code you entered, replace "ugly" with "lame". it's a different mp3 encoder, might work better for you.

---

### Post by SeanTater on 2007-02-24
Try grip too, it's the only one I can think on on gnome at the moment (I use KDE), but as alternatives, you may try kaudiocreator, konqueror, krusader, dolphin(?), kaffeine(?), amarok(?)

---

### Post by Heedbanger on 2007-02-24
Thanks for the help guys.

I replaced "ugly" with "lame" and tried again the file size went down to 3.4mb.

---

### Post by Barbalbero on 2007-02-24
I've the same problem, but I already created the mp3 profile with "lame", even so a single song it's about 45mb, and it's unplayable by totem/rhythmbox... :(

---

