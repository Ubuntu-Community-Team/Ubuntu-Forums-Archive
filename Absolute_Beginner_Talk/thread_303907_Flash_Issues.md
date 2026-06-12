---
title: "Flash Issues"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by snapcase16 on 2006-11-21
I apologize if Flash problems appear frequently, but I can't seem to solve mine. I am using Ubuntu 6.06 as well as Firefox 1.5. I can view videos on sites such as YouTube, but I can't on the photobucket website. When I attempt to view a video on photobucket, I can hear the sound but I only see a gray screen. Both sites appear to use Flash so I don't understand the inconsistency. My About Plug-ins reveals the following in regard to Flash:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I have no previous versions of Flash installed either. When I was using an earlier version, I experienced the same problem. Thanks for any possible help!

---

### Post by snapcase16 on 2006-11-23
Any ideas?

---

### Post by PrinceArithon on 2006-11-23
Sure, I got 3 possible ideas 2 ideas for sure.

Possible idea: Upgrade to Edgy

For sure idea no. 1:  Install Firefox 2.0

sudo apt-get install firefox  (please don't shoot me if that is wrong)

For sure idea no. 2:  After Firefox 2.0 is installed type this into your terminal

wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 


Anyway just to explain.  No matter if you upgrade to Edgy or not you still need Firefox 2.0 and you need to do the last step.  The last step installs a beta flashplayer 9.  So far the beta seems to work really well without bugs, so I wouldn't worry too much about it.

---

### Post by Irony on 2006-11-25
Thanks PrinceArithon your advice worked.

I'm on Firefox 1.5.0.8 I downloaded the thing as you instructed and replaced my libflashplayer.so in /usr/lib/flashplugin-nonfree with the extracted libflashplayer.so - its about 6.6 compared to 2.1 MB of the old libflashplayer.so.

Started up Firefox 1.5.0.8 and I now have sound in YouTube.

---

