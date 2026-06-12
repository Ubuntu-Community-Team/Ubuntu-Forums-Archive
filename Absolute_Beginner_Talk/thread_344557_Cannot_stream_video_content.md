---
title: "Cannot stream video content"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-01-23
First off I apologize for the upcoming lack of technical information.

So far I have got everything I would ever need of my desktop to work with ubuntu. However, there is one last gripe that has remained unresolved. I am unable to stream mpeg video within my Firefox browser. I have tried a number of media players ranging from the default totem to gxine, mplayer, and vlc. However, none of them have ever worked. Totem just leaves a blank space were the embedded video is meant to be as does mplayer. VLC leaves a cute note saying no video dectected, and gxine runs the video (shock) but the sound cuts out withing two seconds of starting with an error message stating that the audio device is unavailable. I believe I have all the necessary codecs, so I have no idea what is wrong. I'm also worried that with the constant changing of media players I have become stuck with totem as default for browsing somehow as I can no longer get gxine or the others to work.

](*,)

---

### Post by Sasa_Ivanovic on 2007-01-23
I use mplayer and it works fine. Have you downloaded the codecs of mplayer supplied on their site ? And have you put them in the right dir ? Also you should set some things up with mplayer when you install it.

Does video work at all, or only in firefox ?

---

### Post by deadgobby on 2007-01-23
Mplayer works great. You may need to update you flash player to flash #9. 
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
Gobby

---

### Post by Hellcom on 2007-01-23
I know you're going say RTFM, but how do you install the video codecs? I have no idea what the readme wants me to do or how to do it.

---

### Post by stoer on 2007-01-23
Hi Hellcom,

mplayer should work fine so long as all the codecs are in place....

look here,
[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)
You'll find something  like this.......
...."If you want to install Mplayer with plug-in for Mozilla Firefox run the following command

sudo apt-get install mozilla-mplayer       "

have you checked this site out?
[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)

or Automatix2?
[http://www.getautomatix.com/](http://www.getautomatix.com/)

personally, i like Kafeine (a KDE app but works fine in Gnome)
"Kaffeine is a media player for KDE. While it supports multiple player engines, its default engine is Xine, giving Kaffeine a wide variety of supported media types and letting Kaffeine access CDs, DVDs, and network streams easily.

Kaffeine can keep track of multiple playlists simultaneously, and supports autoloading of subtitles files for use while playing video.

Homepage: [http://kaffeine.sourceforge.net](http://kaffeine.sourceforge.net) "

Download it via Synaptic if you want to give it a try.

Succes!

---

### Post by deadgobby on 2007-01-23
> **Hellcom said:**
> I know you're going say RTFM, but how do you install the video codecs? I have no idea what the readme wants me to do or how to do it.

NO! If a poster says to RTFM. They are warned and if it happens again. Then the crazy cow will come and eat them.  You will not get RTFM ever here in Ubies forums. You'll get links to read up and try. That is a very naughty thing to tell some one. To a  Noob or the advance. Either way. Here you are going to get help on what you require. 
Gobby

---

### Post by XstatyK on 2007-01-23
> **stoer said:**
> Hi Hellcom,

mplayer should work fine so long as all the codecs are in place....

look here,
[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)
You'll find something  like this.......
...."If you want to install Mplayer with plug-in for Mozilla Firefox run the following command

sudo apt-get install mozilla-mplayer       "

have you checked this site out?
[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)

or Automatix2?
[http://www.getautomatix.com/](http://www.getautomatix.com/)
Succes!

I agree with the Automatix2 route as that is what I have done a couple of times right after a fresh install and it has been working fine for me as well.

---

### Post by stoer on 2007-01-23
Hi Hellcom,
just did a little googling and found this,
might be what you're looking for?

[http://www.ubuntuforums.org/showthread.php?t=76946&highlight=firefox+1.5](http://www.ubuntuforums.org/showthread.php?t=76946&highlight=firefox+1.5)

Sucess

---

### Post by Hellcom on 2007-01-23
Thanks everyone, that really helped. I have gotten rid of the broken totem plug in and have successfully installed mplayer. Everything is working great now.

---

