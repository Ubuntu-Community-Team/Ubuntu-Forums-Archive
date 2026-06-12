---
title: "Video problem"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-02-24
Seemingly randomly after a while in any one session, i can't watch videos because the screen goes liike this 
[http://img175.imageshack.us/my.php?image=screenshotbk3.png](http://img175.imageshack.us/my.php?image=screenshotbk3.png)

The sound works fine though, what can i do?

---

### Post by skymera on 2008-02-24
That happens to me.
i download them to my desktop and watch with VLC

but finding the cause will be nice :wink:

---

### Post by Falc7 on 2008-02-24
I downloaded to desktop and watched with vlc, the same thing happens :-(

---

### Post by ScottyBoyNow on 2008-02-24
Goto Add/Remove programs and search for codecs.

Install all the codec packs that you see, install Xine backend and the restart your PC.

---

### Post by justsomedude on 2008-02-24
I highly recommend the MPlayer plugin for Mozilla, works like a charm.

Remove totem-mozilla:

```
sudo aptitude remove totem-mozilla
```

In case you have it installed, also remove the VLC plugin for Firefox:

```
sudo aptitude remove mozilla-plugin-vlc
```


Then, make sure there are no leftovers from these plugins in **/usr/lib/mozilla/plugins** and **~/.mozilla/firefox/plugins** to be found.


Install MPlayer for firefox:

```
sudo aptitude install mozilla-mplayer
```

Plays pretty much everything, including the example you posted in the screenshot just fine, I tested it... :)

---

### Post by Falc7 on 2008-03-03
thanks for the advice, unforuntately it only happens sometimes, and it isen't related to firefox, just playing things which i have downloaded in totem or vlc player sometimes leads to that screen

---

