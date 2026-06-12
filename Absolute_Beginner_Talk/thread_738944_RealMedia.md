---
title: "RealMedia"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by UpSignal on 2008-03-29
Hello there my friends. Here's what's going on:

    I wanted to watch some RMVB movies, so i followed a tutorial on how to install realplayer from the BIN file available on their website. The installation went good, but when i opene the movie, the video playback was very slow and laggy, and the audio lagged too. I turned it off, removed realplayer, and installed the DEB file instead. Same realplayer version. and also the same problems.
    Well, i didn't gave up, so i went to another tutorial: getting Mplayer up and working. Piece of cake, but the problem is: You can't stretch the video... no full screen, you just have to watch the video on that tiny window. (unless of course, you do some tricks with the compiz-zoom feature). so, i hated Mplayer.
    I have a friend with Gutsy too, and he has real player working with no lag.  i don't understand why this is happening to me!
    Some info about my configuration:

 - Ubuntu Gutsy installed with all updates
 - Gstreamer codecs installed. and a couple of other..like w32 and so on
    It's a fresh gutsy install, made yesterday. so i could be missing some extra codecs or video configurations, i don't know dudes, please help me!

---

### Post by bumanie on 2008-03-29
Try vlc player it plays just about every codec there is. There is also a player named helix, which is an open source player that is meant to play real media files.
> sudo apt-get install mozilla-plugin-vlc (installs as browser plugin + vlc player) and/or
> sudo apt-get install mozilla-helix-player (installs as browser plugin + helix player)

---

### Post by haha123 on 2008-03-29
Is your graphics card blacklisted?if that is correct try this...open up real player  tools>preferences>hardware>unmark  "use xvideo" then click apply.now try to play in real player..

---

### Post by UpSignal on 2008-03-29
> **bumanie said:**
> Try vlc player it plays just about every codec there is. There is also a player named helix, which is an open source player that is meant to play real media files.
 (installs as browser plugin + vlc player) and/or
 (installs as browser plugin + helix player)

Installed. helix does not read my RMVB file. it says "the player doe snot have the capabilities to play this content"

I'm gonna try vlc player now

Is your graphics card blacklisted?if that is correct try this...open up real player tools>preferences>hardware>unmark "use xvideo" then click apply.now try to play in real player..

That didn't work either

---

### Post by UpSignal on 2008-03-29
Solved dudes. i'm using Xine ;)

---

