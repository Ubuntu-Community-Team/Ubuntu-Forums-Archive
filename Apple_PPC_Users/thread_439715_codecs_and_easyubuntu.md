---
title: "codecs and easyubuntu"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by trash on 2007-05-10
ok i've read stuff should get installed through add/remove but that didn't happen and i've just tried easyubuntu but it doesn't seem to have repos for feisty. Can anybody clarify?
i've installed libdvdread but ofcourse i'm missing libdvdcss but I can't find it anywhere, i'm also having trouble playing avi files with vlc,mplayer, totem... all installed through add/remove??

---

### Post by dfreer on 2007-05-11
there is a script inside of libdvdread directory that installs libdvdcss (the script name is called install-css.sh I believe, but I can never remember the blasted directory that it is in. It seems like it is in different place depending on which version of ubuntu you are using, feisty/edgy/dapper etc)

try finding a howto in google that deals specifically with that script. you can also just google for libdvdcss2, which isn't included anywhere in the official repos for legal reasons.

---

### Post by trash on 2007-05-11
Thanks very much:).. dvd's play better than ever in Feisty!

for libdvdcss2
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

going to try another avi file since dvd's play no prob

---

### Post by stmiller on 2007-05-11
Everything is in the PPCFAQs in the link below.

---

### Post by trash on 2007-05-11
thanks missed that link

---

### Post by trash on 2007-05-11
got all the codecs but all players still quit while trying to open all avi's.

vlc in terminal gives me 'iilegal instruction'

---

### Post by dfreer on 2007-05-11
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

hmmm. what are the .avi's encoded with (divx etc)?

---

### Post by trash on 2007-05-11
hard to tell with the files i already had downloaded because i can't open the properties window to see. But dvd's now play just dandy.
I did install the ppc-codecs

---

### Post by trash on 2007-05-13
work-araound is to install gxine and xine-ffmpeg plugin.

---

