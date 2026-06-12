---
title: "MPlayer (gmplayer) GUI problem in Ubuntu Gutsy"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Pacifik on 2008-04-17
Hello friends,
I am new to Ubuntu linux. I have been using opensuse and Debian Etch linux since 2 yrs (Etch from the date it is released officially).

I have installed Ubuntu gutsy few months back. Every thing is working great except MPlayer (gmplayer). When I try to play a movie file (say movie.avi file) from just clicking on it, it does not play. A windows pops up saying it cant play the file. But if I try to open the same file from the command line by the command 
>gmplayer movie.avi
it plays.

Note: I have installed all the codecs. (for eg. libdvdcss2, w32codec, etc)

Please guide me to find the problem(s).
:)

---

### Post by aeiah on 2008-04-17
do you have any unusual characters or spaces in the filename? if so, you can do this. it worked for me, but doesnt work for everyone apparently. you can also downgrade, because apparently its a new error:

Open /usr/share/applications/mplayer.desktop
change "Exec=gmplayer %U" to "Exec=gmplayer %f"

---

### Post by Pacifik on 2008-04-17
Thanks aeiah,
Your suggestion worked. I have edited the file /usr/share/applications/mplayer.desktop accordingly.
The problem is fixed.

---

