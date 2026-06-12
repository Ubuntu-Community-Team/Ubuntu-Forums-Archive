---
title: "Dapper, mplayer-plugin, streaming problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by vv88 on 2007-04-23
Well, it's been back and forth between Dapper and Feisty and I decided to stick with Dapper b/c of wireless troubles (trouble w/ recognition, ndiswrapper, etc).  However, that's a whole seperate issue.  Overall, I've been very happy with Ubuntu (been using it for six months, linux for about a yr).

**My Problem**

Keep in mind this is Dapper.

Following a suggestion in another thread I went into terminal and changed my default audio device to my USB speakers (which worked great, btw).  Next I installed all necessary codecs for mp3, divx, etc.  Following that, I installed the necessary mplayer plugin for mozilla.  I also installed Java and flash plugins as instructed in the online docs through Synaptic.

In the first few runs all video and audio streams played flawlessly (avi, mpeg, mp3, etc).  However, recently mplayer has begun to open, transfer file data, and just show "download complete".  No music/audio or video plays whatsoever.  Furthermore, firefox seems to lockup and I have to force quit the program.

I'd also like to mention that flash is having problems playing mp3s also (no sound).

Any ideas or pointers?  I imagine this has more to do with a codec package being screwed up than the flash or mplayer plugin.  **However mplayer can handle local divx and mp3 files just fine.**  It's the streaming files I'm having problems with.

---

### Post by harishg on 2007-04-24
Do you have any other playes installed alongside mplayer? One thing you can do is check in firefox by typing about:plugins in the address bar.I had problems with multiple players installed.One possible option is using about:config in the address bar and changing the priority of theplayers.But I'm not sure how to go about it exactly.:(

---

### Post by vv88 on 2007-04-24
Thanks for the quick reply, it's a start.

I'm showing mplayerplug-in 3.17 for all audio/video handling except for shockwave flash (libflashplayer.so).  I also have the Java plugin, but that's the extent of the about:plugin.

---

### Post by harishg on 2007-04-24
Was m-player playing streaming files before ? Usually playing streaming files can sometimes cause problem.Did you install all the restricted codecs and formats  using automatix or easyubuntu?

I also keep having problems with streaming files on many sites even though I have the necessary codecs for them. ;(.I can check the site to see if my machine plays it.

---

### Post by vv88 on 2007-04-24
Well I started with two main issues.

1) Divx (avi), Mpeg wouldn't play through a stream
2) I wasn't getting sound/video through flash

The situation is *somewhat* resolved through an alternative app.  But it took a while to get there.  Basically, this is what I did.

I uninstalled flash-plugin (nonfree), mplayer plugin, mplayer, all necessary codecs, lame, and mencoder.

I rebooted the pc and installed the required codecs, then installed the **Mozilla xine Plugin**. then the flash-plugin.

This allowed me to play video streams through xine (which is pretty decent in my opinion).  The only problem was, I wasn't getting sound through my USB speakers (which were still configured properly as default), but through my terrible PC speakers.

I went into terminal and re-saved my alsa config.  Then I rebooted again and now everything is playing great through xine (not mplayer).

Please don't consider this as a tut or great advice.  Once you start experimenting, it's hard to relay the specifics.  However, this is how my issue was resolved.

Thanks for the help harishg, it seems mplayer was hanging on something.  btw, for most packages I use synaptic, but find myself in terminal tweaking/installing more and more each day.

---

