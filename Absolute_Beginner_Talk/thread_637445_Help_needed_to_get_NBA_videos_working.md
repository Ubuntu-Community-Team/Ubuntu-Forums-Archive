---
title: "Help needed to get NBA videos working"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by GlorytheWIz825 on 2007-12-11
I can't watch the highlights and the top 10 from [www.nba.com](www.nba.com). I simply get a black video screen that says "No Video". 

Already installed the following plugins:

sudo apt-get install sun-java6-plugin
sudo apt-get install flashplugin-nonfree
sudo apt-get install mozilla-plugin-vlc
sudo apt-get install mozilla-mplayer
sudo apt-get install mozilla-helix-player

Any ideas? Thanks!

---

### Post by randcoop on 2007-12-11
I can only get these videos to work under Firefox using MediaPlayerConnectivity.  That's an extension that you can get from addons.mozilla.org.  Once you've added it to Firefox, you won't get that (no video) screen.  Instead, the addon will take over and let you run whatever program you want to watch the videos.  In this case, I configured the addon to use Kmplayer (I'm using Kubuntu).  But it worked fine.

Hope that helps.

---

### Post by GlorytheWIz825 on 2007-12-11
Thanks for the help. The videos are playing using mplayer. Quality seems lower than what I'm used to seeing on XP, but it's still watchable. 

Thanks again. :)

---

### Post by Flying caveman on 2007-12-11
I can watch them, but i did see that to see some of the photo galleries you need M$ $ilverlight. 

Good thing, I don't like basketball anyway.  e-mail the webmaster and ask why they can't just use flash like everybody else.

I think mine played in Totem xine, I don't know it just sort of worked.

---

### Post by Sentientv2 on 2008-02-02
Flying, not sure how I missed your observation, but I found it on another site and came back here to share the good news,

```
sudo apt-get install totem-xine totem-mozilla
```

works like a charm. No firefox mediaplayer connectivity add-on needed.

Rejoice!!

---

### Post by GlorytheWIz825 on 2008-02-27
The videos are now playing in great quality, same as what I was getting with XP. Unfortunately, I cannot get any sound to come out. Am I missing some audio codecs?

Thanks in advance.

---

### Post by GlorytheWIz825 on 2008-02-27
Forgot to mention that I am now using totem as my media player. So installed totem using:

sudo apt-get install totem-xine totem-mozilla

---

