---
title: "Ripping/Listenening to AAC (m4a) files in Kubuntu"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by rorschach on 2006-05-30
Hi, I am ripping my music library anew, and I am running into a few minor roadblocks:

First, I am using Sound Juicer to rip my files, and I followed the wiki and am ripping to AAC (.m4a). How can I check/control the bitrate that I am ripping at?

Second, I like amaroK - especially the collection management - however I can't seem to get it to recognize the m4a files at all, nor will it play them if I browse over to them and select them - I do have both gstreamer0.8-faad and gstreamer0.10-plugins-bad-multiverse installed. What's going wrong?

(Note: I did check my engine for amaroK, and it is using xine (I do also have libxine-extracodecs) - however I don't have the option to change to gstreamer in the drop-down. Is there something I'm missing? or is there a way for me to 'force' the engine to change via the command line?)

Help? I really want to encode in AAC

(Well, I would *really* like ogg, but, ogg won't work in my car's cd-player - AAC just works more places, and sounds better than mp3)

---

### Post by mostwanted on 2006-05-30
Amarok uses xine in Dapper, not gstreamer. You need to install libxine-extracodecs (or similar, the package is called something like that).

---

### Post by rorschach on 2006-05-30
I have libxine-extracodecs installed but it still does not work

---

