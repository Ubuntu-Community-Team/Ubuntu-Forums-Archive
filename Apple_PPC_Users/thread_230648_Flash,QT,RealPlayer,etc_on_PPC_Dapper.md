---
title: "Flash,QT,RealPlayer,etc on PPC Dapper"
date: 2006-08-06
forum: Apple PPC Users
---

### Post by meshica7 on 2006-08-06
Hello folks!

I have been running Dapper on a Power Mac G4 for about a month or so and have a question.
It seems that all the plug-ins (Flash,QT, etc) for Firefox,Mozilla and the like are not supported for the PPC.What can I use to view and experience multimedia content on the web.

Thanx!

Juan

---

### Post by 3rdalbum on 2006-08-07
Unfortunately, at the moment, there's nothing you can do. If you don't mind virtualising the Mac OS on your machine, you could install Mac-On-Linux and surf the web through that?

It'll be a fair wait until Gnash (an open-source implementation of Flash) is ready, and there's very little possibility that the Helix folks will fix their PPC RealPlayer, so maybe the best option for you would be to buy a second-hand PC? I know that sounds like a cop-out, but unfortunately that's the situation.

By the way, don't try installing GPLFlash; it doesn't play anything, and it just makes your browser unstable.

---

### Post by Ububurns on 2006-08-07
I have compiled and installed gnash on PPC, with the firefox plugin.

It is worth noting that Gnash is a work in progress. Yes, it can play some flash files, but without sound, and without user interaction (ie: flash games or "Click to play" etc.)

Regardless, it's great to know that you can at least partly knock out one of the top three "hard to get"'s for PPC (ie: flash, java and wmv3 playback).

Please find gnash-0.7.1_powerpc.deb [here]("http://filexoom.com/files/11540/gnash-0.7.1_powerpc.deb").

As it doesn't know what packages it needs, you will also have to install libgtkglext1 (it should be in synaptic).

To check that this gnash has installed correctly, in the location bar of Firefox type in "about:plugins" and look for an entry titled "Shockwave Flash" that refers to gnash.

Let me know if this works for you - it works for me, and other people!

---

### Post by trash on 2006-11-01
> **Ububurns said:**
> I have compiled and installed gnash on PPC, with the firefox plugin.

It is worth noting that Gnash is a work in progress. Yes, it can play some flash files, but without sound, and without user interaction (ie: flash games or "Click to play" etc.)

Regardless, it's great to know that you can at least partly knock out one of the top three "hard to get"'s for PPC (ie: flash, java and wmv3 playback).

Please find gnash-0.7.1_powerpc.deb [here]("http://filexoom.com/files/11540/gnash-0.7.1_powerpc.deb").

As it doesn't know what packages it needs, you will also have to install libgtkglext1 (it should be in synaptic).

To check that this gnash has installed correctly, in the location bar of Firefox type in "about:plugins" and look for an entry titled "Shockwave Flash" that refers to gnash.

Let me know if this works for you - it works for me, and other people!

I was able to download and install the file but it doesn't work too well and only in firefox. Is there a newer deb anywhere?

---

### Post by cmorgan47 on 2006-11-01
there's no good way to do it natively, but macOnLinux is excellent.  easy to install using [this guide]("https://help.ubuntu.com/community/MacOnLinuxHowto")

takes a minute to start up...not much longer than OSX typically does, but once it's running switching between OSes is about as easy as switching between apps.

---

### Post by kellogs on 2006-11-01
last cvs version of gnash autoinstalls itself to a proper directory and does show in firefox, you only have to compile it with --enable-plugin and that's it. Still is not interactive enough for games or movies, but almost the majority of non interactive flash content works.

IBM Java is a little unstable at the moment, havent checked other free javas.

I tried mplayer with some realplayer movies that even realplayer could not play well and mplayer plays perfectly (even some QT 7 movs) so use mplayer :P.

---

### Post by trash on 2006-11-01
> **cmorgan47 said:**
> there's no good way to do it natively, but macOnLinux is excellent.  easy to install using [this guide]("https://help.ubuntu.com/community/MacOnLinuxHowto")

takes a minute to start up...not much longer than OSX typically does, but once it's running switching between OSes is about as easy as switching between apps.

well better than nothing i guess:).

---

### Post by stmiller on 2006-11-02
[http://www.helixcommunity.org/](http://www.helixcommunity.org/)

There's a PPC Linux version of Realplayer on this site. Works great.

Also, install the mplayer mozilla plug in. I can view quicktime content with that on my machine.

---

### Post by ssam on 2006-11-02
if you want to pester adobe to release flash for linux fill in a request at [http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform)

---

### Post by anders_gud on 2006-11-02
> **stmiller said:**
> [http://www.helixcommunity.org/](http://www.helixcommunity.org/)

There's a PPC Linux version of Realplayer on this site. Works great.


[https://helixcommunity.org/2005/patents/](https://helixcommunity.org/2005/patents/)

---

### Post by 3rdalbum on 2006-11-03
The PPC version of Realplayer works great for stmiller, but many other people haven't had any luck with it.

I forgot to mention, VLC apparantly has reverse-engineered Windows Media Video support, even on PowerPC.

---

### Post by stmiller on 2006-11-03
Yes VLC will play just about everything. Even Divx files.

---

### Post by anders_gud on 2006-11-04
> **3rdalbum said:**
> The PPC version of Realplayer works great for stmiller, but many other people haven't had any luck with it.
You can point [gxine]("http://xinehq.de/") to the realplayer libs from the Realplayer 8... 
File->Configure->Preferences->decoder.
/opt/RealPlayer8/Codecs/
...if realpayer is installed in /opt. Much nicer ;)  


> **3rdalbum said:**
> 
I forgot to mention, VLC apparantly has reverse-engineered Windows Media Video support, even on PowerPC.
Almost all WMV codecs are supported now, read more [here]("http://codecs.multimedia.cx/")

---

### Post by stmiller on 2006-11-04
VLC on PPC ubuntu plays windows media 9.1 audio files for me. I haven't tested anything else. Hope this helps,

---

### Post by markd1216 on 2006-11-05
Can you guys be a bit more specific where to find and how to install from the helixcommnity.org site.  I hunted around quite a bit but nothing jumped out at me and for the ones I tried could not get an install.  I quite new at this --- running linux on a graphite iMac 600 MHz with 268 MB RAM.  Might this hardware be too old? Thanks ... Mark

---

### Post by gerghk on 2006-11-05
I've tried installing VLC via synaptic, the version is 0.8.6-svn.  I know for a fact that VC-1 support is built into 0.8.6.

However, everytime I open a video file in vlc, it crashes and returns an error in the command line saying "Illegal Instruction"

I've tried multiple video formats, so it's not just wmv9 doing it.

I'm using an iBook G3 800Mhz, has anyone else ever run into this problem?

---

