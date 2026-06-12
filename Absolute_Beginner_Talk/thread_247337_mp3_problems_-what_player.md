---
title: "mp3 problems -what player"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-30
Hi,
Right Im using the Ubuntu hacks book from o rielly (great book btw).
It told me to install these general purpose libaries and tools:

totem-xine
vorbis-tools
sox
faad
lame
imagemagick
ffmpeg
mjegtools

It also said install some gstremer plugins and the w32 codecs.

When I click on a wma file mplayer loads up and plays the song.
When I click on a mp3 file rythm box loads up but wont play the song.
Rythm box will play ogg files though.
I tried importing my music directory into rythmbox but it only recognises ogg files.](*,) 

Can any body help me?! I just wanna set everything up so I can click on an audio file one program will play and let me enque things.

thanks for any help!

---

### Post by benfindlay on 2006-08-30
I personally use VLC, it plays all music codecs I've come across, and all video formats, with the exception of Microsh*te's proprietary wmv format. Its enqueueing method is a little different to what you may expect (click and drag from file folders into the playlist) but it works like a peach and is extremely low-resource friendly!

Hope this helps!

---

### Post by Nytram on 2006-08-30
[QUOTE=bplus;1442244]Hi,

It also said install some gstremer plugins and the w32 codecs.
ong.
When I click on a mp3 file rythm box loads up but wont play the song.

One way I used to play mp3's:
Applications>>Add/Remove
search for gstreamer
Apply the package that mentions mp3 codecs (gstreamer extra plugins)

HTH

Martyn

Alternatively theres Automatix which can install a number of codecs

---

### Post by Fully216 on 2006-08-30
Since mp3 is a licensed format (not free), it is not natively supported by ubuntu.  You have to install support for it.  There is a great discussion on media players and formats found below (even a section on the mp3 format).

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This will tell you not only how the get the format working, but also introduce you to many different player options.  Personally, I like amorak, but each to their own.

Nytram is correct, you need the gstreamer package.

Hope this helps.

---

### Post by PPAAUULL on 2006-08-30
Just use Automatix. It does like eveything a newbie wants and gets just about everything working. I use it all the time when I install Ubuntu on a friends PC. Saves me time.

---

### Post by Fully216 on 2006-08-30
FYI: automatix works well as long as you are not using an amd64 system (like me), otherwise it will cause some serious problems, especially with flash.

---

### Post by PPAAUULL on 2006-08-30
Ya just watch for that.

---

### Post by bplus on 2006-08-30
cool, thanks!
If I install automatix will mess up any of the codec I ve already installed?

---

### Post by Fully216 on 2006-08-30
Most likely no, but I cannot give you a definitive answer because I have not used it.  I would assume it would upgrade any old versions and skip if it is newer.

---

### Post by PPAAUULL on 2006-08-30
No it will not screw the codecs up that you have already installed. I use it all the time. great tool. good luck with it.

---

