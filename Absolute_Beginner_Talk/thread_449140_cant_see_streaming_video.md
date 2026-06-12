---
title: "cant see streaming video"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-19
hello guys.. i went to see video on this site

[http://stage6.divx.com/](http://stage6.divx.com/)

but it doesnt work.. when i click on the play icon it goes blank..any know how i can fix this.. is it cause of lack of codecs that i have ?

---

### Post by tchoklat on 2007-05-19
probably will be. Try using getautomatix.com to load all your needed codecs, that is what I did and all is fine to date!

---

### Post by HunkieChan on 2007-05-19
thanks bro

---

### Post by wormser on 2007-05-19
For Mplayer the right files for playback sometimes get put into the mozilla plugin folder instead of the firefox plugin folder.  The following seems to be a fix.

If you do not see the mplayerplug-in-dvx.* files in /usr/lib/firefox/plugins and they are in /usr/lib/mozilla/plugins then use the following commands to create a symbolic link to the mozilla/plugins/mplayerplug-in-dvx.* files.

```
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
```

---

### Post by Michaelt74 on 2007-05-20
Try VLC, it's the easiest player to configure, this may help:

Multimedia codecs

Something which caused anguish in the past has been made simple.

Click on Applications>Add/Remove Applications>search for Ubuntu Restricted extras, install these. You will now have most the of the codecs needed to play streaming video and audio. In the same application, search for and install the Flash plugin. Search for and install the VLC Media Player, I found this the most useful and reliable media player to use, especially for streaming.

Firefox media streaming

Search for and install the media player connectivity add on in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

When it’s installed use the wizard and configure VLC to play all streaming video.

*Note I encountered a problem which resulted in degraded quality when I stream video from Yahoo using VLC, fortunately I found a fix; this may or may not work for you. When you open a link to streaming content from Yahoo, click on ‘Video Quality’, the option next to ‘help’ (your current preference / detected streaming rate is displayed). Mine is 300k. Click on 100k, then ’select’, an advert may reappear, when it’s finished, click on ‘Video Quality’ again and select your original settin (mine was 300k so I clicked it again), then ’select’. When you click on the small ‘play button’ the quality should be greatly improved.

---

### Post by HunkieChan on 2007-05-20
thanks guys ill try it out

---

