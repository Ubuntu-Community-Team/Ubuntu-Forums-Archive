---
title: "how to get mplayer to play movies?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by enetic on 2007-10-13
Is there a way for mplayer to automaticly open a video-link in a new window? Forexample if i click on a link, mplayer (the software) automaticly pops up and plays it (standalone from swiftfox)? I do not want it to be played integrated in swiftfox.. 

how can i do this?

---

### Post by NavmaN on 2007-10-13
So you want it to play in the browser or standalone?

If the former is you intention, then install the mplayer swiftfox/firefox plugin. You can get it from automatix2 or manually from the mplayer website.

Hope that helps,
Van

---

### Post by enetic on 2007-10-13
i want it to open in mplayer seperatly from the browser. i want it nothing to do with firefox

---

### Post by enetic on 2007-10-13
right now i got it to work with norwegian NRK television through their webpage [www.nrk.no](www.nrk.no) , but it seems that im short of some plugins because mplayer wont play nothing. im trying to play a videoclip from my computer but it wont. right now i want it to work with every link i try, not just the NRK links

---

### Post by Abild on 2007-10-13
If you want to open an embedded video in an external player I can only recommend the Media Player Connectivity plugin. As for mplayer not being able to play specific videos, try installing the w32codec package (if you run 64bit ubuntu you'll want w64codecs) 

w32codecs is available from
[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb)
(install with dpkg -i <package name>)

Finally, I'd like to point out that if you want to play streaming wmv encoded videos vlc currently does a much better job than mplayer. For other formats like real media, mplayer with w32codecs is the way to go.

---

