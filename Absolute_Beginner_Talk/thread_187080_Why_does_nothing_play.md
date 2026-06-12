---
title: "Why does nothing play"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Mr Sprout on 2006-06-02
Why does nothing play in totem? I've installed ubuntu 6.06 on my Powerbook and it's all working great apart from that no videos will play. At all. I've installed the ffmpeg which says it will make play MPEG4 files. When I go to play a MPEG4 file I get a message in totem about the required codecs not being there! 

Any help would be appreciated. ](*,)

---

### Post by AndyCooll on 2006-06-02
Might be worth trying Automatix, part of that includes installing codecs for pretty much anything you could wish to play.

:cool:

---

### Post by Jason_25 on 2006-06-02
ffmpeg just converts video files.  The ffmpeg plugin for gstreamer does that, but you can get playback of pretty much everything by downloading the gstreamer good, bad, and ugly plugins instead.

---

### Post by IYY on 2006-06-02
Ubuntu supports these restricted formats, but it would be illegal to include it in the installation. This is why you have to do the following after you install the operating system:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by mscman on 2006-06-02
[QUOTE=AndyCooll]Might be worth trying Automatix, part of that includes installing codecs for pretty much anything you could wish to play.

:cool:[/QUOTE]
Automatix isn't supported in Dapper, only for Breezy.  For an automated install for Dapper, try the [Azureus-Limewire]("http://www.ubuntuforums.org/showthread.php?t=148760") installer.  You can check which packages you want installed, so if you're only looking for multimedia functionality, uncheck the azureus and limewire programs so you don't waste space.

---

### Post by Perfect Storm on 2006-06-02
It say it does: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646) Automatix for Dapper.

---

### Post by Mr Sprout on 2006-06-02
Thanks so much you guys. Never have I had a quicker response to a problem from so many people in so little time on any forum. You guys are awesome. The automatix method worked a charm. Thankyou very much, all of you. :D

---

### Post by mscman on 2006-06-02
[QUOTE=Artificial Intelligence]It say it does: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646) Automatix for Dapper.[/QUOTE]
Wow, my bad.  I could have sworn I double checked right before I posted, but I must have looked at an old thread.  Glad to see it's been changed!  The Azureus-Limewire installer is still a good one though.

---

### Post by dvarsam on 2006-06-02
Hello!

To make your Totem play DVDs, search & install the package "totem-xine-firefox-plugin".

Keep in mind the Restricted Formats.

Good Luck.

---

### Post by Lord Illidan on 2006-06-02
[quote=dvarsam]Hello!

To make your Totem play DVDs, search & install the package "totem-xine-firefox-plugin".

Keep in mind the Restricted Formats.

Good Luck.[/quote]

Actually, it is totem-xine

---

### Post by dvarsam on 2006-06-02
[QUOTE=Lord Illidan]Actually, it is totem-xine[/QUOTE]

NO, it is _NOT_ the same package!

The "totem-xine-firefox-plugin" package is NOT the same package as the "totem-xine" package!

The later is just a Dependency to the "totem-xine-firefox-plugin" package.

And when from the Menu you select "Applications\Sound&Video\Movie Player", the Program that launches & plays the DVD's is NOT "totem-xine" but just/plain "Totem".

---

### Post by AndyCooll on 2006-06-02
[QUOTE=mscman]Automatix isn't supported in Dapper, only for Breezy.  For an automated install for Dapper, try the [Azureus-Limewire]("http://www.ubuntuforums.org/showthread.php?t=148760") installer.  You can check which packages you want installed, so if you're only looking for multimedia functionality, uncheck the azureus and limewire programs so you don't waste space.[/QUOTE]

You are incorrect my friend. There _is_ now a version of Automatix for Dapper, I've used it!

:cool:

---

