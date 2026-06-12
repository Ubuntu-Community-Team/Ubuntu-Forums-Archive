---
title: "problem playing mp4"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2007-05-30
I have a couple of mp4 files taken on my phone, but I cant seem to get them to play, only audio plays, no video.
do I need any codecs to play these files

---

### Post by eye208 on 2007-05-31
> **celticbhoy said:**
> I have a couple of mp4 files taken on my phone, but I cant seem to get them to play, only audio plays, no video.
do I need any codecs to play these files
Probably yes.

Does VLC play them? If yes, you probably need to install GStreamer codecs for ffmpeg to enable other applications to play them too.

---

### Post by celticbhoy on 2007-05-31
How do you work VLC ????

---

### Post by dannyboy79 on 2007-06-07
i can't play a .mp4 file either? I don't even here any sound liek the other guy? I thought Feisty was suppose to have this great multi-media thing that retrieved the required codec's? It worked for the avi file I must say, but not these IPOD files I downloaded from ipodnova.tv. any help anyone? here's a pic from totem
[[IMG]http://img246.imageshack.us/img246/8969/screenshot2jk9.th.png[/IMG]](http://img246.imageshack.us/my.php?image=screenshot2jk9.png)

actually, when I installed the latest gstreamer pitfdll I was able to play SOME of them thru mplayer but I had to make sure that the ALL FILES was used and not the normal VIDEO FILES. I couldn't play them all though which is totally  weird!!! They would show the name within mplayer but nothing was there, and I wouldn't get an error???

---

### Post by ricardisimo on 2007-06-23
Yet another variation on the problem. I have a perfect image and no audio. When I looked through the audio plugins for vlc, it looks like they are all already packaged with vlc itself, so I'm at a loss regarding which one I might help. Thanks in advance for any assistance.

---

### Post by dannyboy79 on 2007-06-25
SOLVED. the reason I couldn't play ALL of the files before is because they were actually not done completely downloading, I am able to play them all. Just install the gstreamer pitfdll and that should do it. I may have even enabled the 
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
repositories for dvd playback as well but I believe the .mp4 issue was due to not waiting until they were all downloaded. NOTE: the above mentioned repo is illegal in the US so be careful if you use it.

---

