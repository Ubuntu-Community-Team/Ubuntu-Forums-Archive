---
title: "[SOLVED] Installed Gutsy, How to play RMVB &amp;amp; MP4 filess"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rahimveron on 2007-10-20
I have just installed Gutsy. Now how do i play RMVB & MP4 files as i have downloaded most of the GStreamer stuff, still totem cannot play them

---

### Post by jayaramk on 2007-10-20
better dowload vlc for viewing files of type mp4,mp3,avi and etc etc.......

install real player for viewing rmvb its present in the repositories or use the synaptic package manager!!!!

---

### Post by rahimveron on 2007-10-20
Realplayer is not in the repo, i think & VLC does not play it either

---

### Post by hanzomon4 on 2007-10-20
Gstreamer can play mp3 and mp4 just fine, i think you only need to try and play one of these files and it will install the codecs for you. 

Rmvb is different however gst can't play these files, but xine+w32codecs can. 

First you need to add the medibuntu repos ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Next run this command to apt-get everything you need to play just about any format```
 sudo apt-get install libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins totem-xine w32codecs libdvdcss
```

Now there's a bug with xine and wmv but it's easy to fix just edit  ~/.gnome2/Totem/xine_config```
 gedit .gnome2/Totem/xine_config 
``` **Change the lines marked in red from this**
```
# priority for win32a decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32a:0**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32v:0**[/color]
``` **To this** ```
# priority for win32a decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32a:5**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32v:5**[/color]
```

Now totem will play all of your videos,even rmvb vids. 
Hope this helps.

---

### Post by rahimveron on 2007-10-22
Thanks but what does that bug do?

---

### Post by hanzomon4 on 2007-10-22
It makes wmv files look all distorted, it's hard to describe. But the fix works........

---

