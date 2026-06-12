---
title: "No sound while playing 3gp Videos"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-18
I can't hear any sound while playing 3gp videos in either Totem or VLC. Do i have to install any codecs or something?

---

### Post by nhandler on 2007-02-19
Try playing a different video file from a different program. If the sound works, it could either be a problem with 3gp or ubuntu. If you are sure it is not a problem wit h3gp, go into a terminal, and type 'alsamixer' (without the quotes). You should see a bunch of bars. Using the arrow keys, scroll right until you get to the 'video bar'. Raise the bar to the maximum using the up arrow key. Then hit Esc to exit. Now try playing the video again.

---

### Post by islander_810 on 2007-02-24
I don't have any option called video in alsamixer. And yeah, the 3gp videos are fine. Do i need to install any codecs to play 3gp videos. I already have these codecs installed.

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs -y --force-yes
sudo apt-get install gstreamer0.10-pitfdll -y --force-yes && rm -r ~/.gstreamer-0.10/ -y --force-yes
sudo apt-get install gxine
sudo apt-get install libdvdcss2


Aren't these sufficient?

---

### Post by louisd11 on 2007-03-15
I got the same prob too. Anyone know any video converter?

---

### Post by islander_810 on 2007-03-17
Prob solved, i played it in realplayer, and i could hear the sound

---

### Post by Kateikyoushi on 2007-03-17
I also use mplayer for it and that does the job, for encoding I would try mencoder.

---

### Post by louisd11 on 2007-03-17
ok donwloading memcoder

---

