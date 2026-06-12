---
title: "mozilla-mplayer problems!"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by SqRt7744 on 2006-03-23
Hello gurus!

(i posted a similar message already, burried deep within another thread, so I'm reposting it here where it belongs and deleting the other, which was out of place!)

I just put Ubuntu on a friends computer and she really liked it... that is until she went to [http://www.milkandcookies.com/topic/0/15](http://www.milkandcookies.com/topic/0/15) and tried to play a clip... it plays the clip (using the mplayer plugin for firefox), but you can't stop the video, and it loops forever, forcing her to use xkill or gnome-system-monitor to kill it. I tried removing the mplayer plugin and using vlc instead, but it isn't as good in other respects, i.e. no buttons widgets, no buffering message, just a black screen with the disconcerting message (no picture), and I can't seem to ff/rw...

I believe the milkandcookies page uses quicktime (it claims quicktime 6 or greater required), but mplayer should be able to handle that.

I had installed: 
-mplayer version is 1.0pre7 (from the repos), and mozilla-mplayer plug-in version 3.17
-all codecs present (well, the video plays so that probably isn't the problem anyway)

In the meantime I've uninstalled the vlc and mplayer plugins and added the firefox extension called mediaPlayerConnectivity, which is a temporary fix at best...

I've told her I'll fix it in a few days, so if anyone has any ideas I would really appreciate it!

Thanks!

---

### Post by gpeck157 on 2006-03-29
[QUOTE=SqRt7744]Hello gurus!

(i posted a similar message already, burried deep within another thread, so I'm reposting it here where it belongs and deleting the other, which was out of place!)

I just put Ubuntu on a friends computer and she really liked it... that is until she went to [http://www.milkandcookies.com/topic/0/15](http://www.milkandcookies.com/topic/0/15) and tried to play a clip... it plays the clip (using the mplayer plugin for firefox), but you can't stop the video, and it loops forever, forcing her to use xkill or gnome-system-monitor to kill it. I tried removing the mplayer plugin and using vlc instead, but it isn't as good in other respects, i.e. no buttons widgets, no buffering message, just a black screen with the disconcerting message (no picture), and I can't seem to ff/rw...

I believe the milkandcookies page uses quicktime (it claims quicktime 6 or greater required), but mplayer should be able to handle that.

I had installed: 
-mplayer version is 1.0pre7 (from the repos), and mozilla-mplayer plug-in version 3.17
-all codecs present (well, the video plays so that probably isn't the problem anyway)

In the meantime I've uninstalled the vlc and mplayer plugins and added the firefox extension called mediaPlayerConnectivity, which is a temporary fix at best...

I've told her I'll fix it in a few days, so if anyone has any ideas I would really appreciate it!

Thanks![/QUOTE]

I really don't know if this will help you, but I was not even able to watch QT videos until I did the following:

```
sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer

```

After I installed those, all was well.

Good luck,
Glen

---

