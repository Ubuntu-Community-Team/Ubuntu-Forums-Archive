---
title: "no video playback in banshee, sound ok"
date: 2012-06-27
forum: Any Other OS
---

### Post by thebestofall007 on 2012-06-27
hello, i was wondering if anyone has been having problems with banshee playing videos with a black screen but with sound intact (and i have seen the issue, but in older versions)? i am also having problems with banshee being slow to switch to the next video when the next/previous is clicked (more likely on a video that has the black screen issue). it also says "idle" in some videos and doesn't want to play them at all (although vlc plays with no problems). it doesn't do this with all the videos.

i have an example of my terminal output that shows a hangup, which happened when the player said "idle" and i clicked on a few other of my video files:

```
lou@lou-MacBookPro ~ $ banshee
[Info  22:33:53.925] Running Banshee 2.4.0: [Ubuntu 12.04 LTS (linux-gnu, x86_64) @ 2012-05-06 11:52:27 UTC]
[Info  22:33:55.228] Updating web proxy from GConf
[Info  22:33:55.247] All services are started 1.086495
[Info  22:33:55.775] AmazonMP3 store redirect URL: http://redir.linuxmint.com/mp3amazonstore/
[Info  22:33:56.125] nereid Client Started
[Info  22:33:56.234] GStreamer version 0.10.36.0, gapless: False, replaygain: True
[Info  22:33:56.281] AppleDeviceSource is ignoring unmounted volume MacBook
[Warn  22:35:25.388] Seem to be stuck loading file:///home/lou/Videos/Chernobyl%20disaster%20incident%20PART%203.mp4, so re-trying
[Warn  22:35:27.399] Seem to be stuck loading file:///home/lou/Videos/playvalue/sony%20vs%20nintendo.mp4, so re-trying
[Warn  22:35:28.702] Seem to be stuck loading file:///home/lou/Videos/How%20to%20replace%20a%20hard%20drive%20in%20a%2015_quot%3B%20MacBook%20Pro.mp4, so re-trying



```

i am using linux mint 13 on a macbook pro 4.1 with nvidia graphics and i have tried the following:

1. entering "gstreamer-properties" in terminal and changing the video output to "x window system - no xv". no go on that.

2. upgrading to the newest 2.4.1 release and downgrading to 2.3.6, and sudo apt-get purging and reinstalling it, and no go on all of those.

3. installing vdpau by typing in the terminal "sudo apt-get install vdpau-va-driver vainfo" and then running vainfo to check the va-driver status, which was good. again no go.

4. made sure to have all the restricted codecs installed, and i do.

i'm stumped and i have looked all over the internet for an up-to-date solution to this annoying problem (like mentioned earlier, i has happened to older versions, but i can't find an up to date solution for it in 12.04/mint 13).

if anyone knows an up to date solution to this, please chime in.

thanks.

---

### Post by thebestofall007 on 2012-06-28
bump.

---

### Post by thebestofall007 on 2012-06-30
bump.

---

### Post by Perfect Storm on 2012-07-01
Moved to Other OS/Distro Talk.

---

