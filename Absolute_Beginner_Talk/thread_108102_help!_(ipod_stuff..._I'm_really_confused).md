---
title: "help! (ipod stuff... I'm really confused)"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-25
Okay, so I've been trying to get something that can work with my ipod and that supports AAC (specifically, .m4a songs). I tried gtkpod, but couldn't get the AAC stuff working (couldn't build from source as I couldn't find all the dependent thingys and I read they conflict with some other packages). I tried Banshee, but it crashes all the time, especially when trying to transfer to my ipod (it even crashes when I'm trying to make playlists sometimes). Let's see, I tried Rhythmbox, but that only reads (reads fine fyi). I tried amaroK, but I can't get it to recognize the ipod. amaroK is what I've been trying to get to work the most. I compiled it from source, the SVN version or whatever (1.4 or 1.37 I don't know, whatever the latest is). I followed a bunch of forums about adding extra options (for certain media type support ( I think) and libgpod (I think) ), I tried setting up my ipod at /mnt/ipod both by linking it to /media/ipod and by editing /etc/fstab. I read [here]("http://www.ubuntuforums.org/showthread.php?t=94028&highlight=amarok+ipod") that it need libgpod compiled. I have libgpod0 and libgpod-common  off the repositories, but I tried manually downloading and compiling libgpod from their website (I did stable release). That didn't work, so I tried the cvs release, but then I realized I didn't know how to remove the original libgpod install and didn't know if amaroK needed to be recompiled or anything,  or how to remove amaroK compiled instead of 'apt-get'ed.

uh ya, sorry bout the long spew of confusion, I don't really know what I'm doing... I would be most appreciative if someone could help me out with this, or at least tell me how to clean out all the useless junk I've acquired so I can start over.

Thank you in advance :)

---

### Post by timetunnel on 2005-12-25
I'm not sure if I understand what you really want. If you just want to be able to maintain the files on your ipod, you just have to install package "gtkpod" with synaptic package manager and that's it. The ipod is mounted at /media/ipod, so just put that into the preferences of gtkpod and it works. For playback of aac/m4a files in Rhythmbox, gstreamer0.8-faad has to be installed as well. 

amarok isn't able to play aac files so far. 

As for all the compiling stuff you've done: no idea how to revert that except for a new clean install (either of the packages that contain the files you recompiled or of the whole system). You really shouldn't compile all these things if you don't know what you're doing. You can really mess up your system this way.

---

### Post by qiemem on 2005-12-25
oh heh, sorry for not being clear.

The reason I can't use gtkpod is that it doesn't support AAC, thus I can't transfer a large part of my music library to my ipod (I can't sync up correctly). I compiled the svn version of amaroK because it does support AAC formats. I got AAC working fine with Rhythmbox, its just Rhythmbox can't write to the iPod, so that doesn't help. Besides, amaroK is a better all around music player, so I'd prefer to use that anyway if I can get the iPod support working.

So, overall, I need something to transfer songs to my iPod which supports AAC files. I'd prefer to get amaroK working, but if that's not possible, that's fine, just as long as I get something working.

Hope that clears up what I'm trying to do.

---

### Post by timetunnel on 2005-12-25
Ok. I see. I haven't used gtkpod on Breezy so far and am quite surprised now to see that it's really lacking AAC support. There used to be a package for Hoary called gtkpod-aac, but it doesn't exist anymore anywhere.
As this is news to me as well I can't help you, sorry.

---

### Post by gpw797 on 2005-12-26
Get amarok working, there are lots of threads on that here.. then I recommend using YamiPod to sync to ipod and it supports aac.

YamiPod is here:

[http://www.yamipod.com](http://www.yamipod.com)

Yami is slow but works all the time gtkpod doesn't always work (for me)

---

### Post by qiemem on 2005-12-26
Ya I tried Yamipod, but it crashed after configuring my ipod and I had to wipe the thing before anything would recognize it again... so uh... but I'll give it another try.

---

### Post by qiemem on 2005-12-26
Okay, so I tried YamiPod again, and everytime I try to sync, at about 30%, it errors: "Please delete the current profile and recreate it. This will only happen once." Or something like that... Anyway, this may not be the place to ask this, but anybody happen to know what's going on here? What profile is it talking about?

---

### Post by gpw797 on 2005-12-26
did you try the YamiPod board? Also the guy that wrote that thing is more than willing to help and answer queswtions.

---

