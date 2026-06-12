---
title: "Playing media on the web"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by TWO on 2007-11-08
I've been using Ubuntu for a few months now. I've overcome most of the issues I've had with my pc and the OS however there is just one that remains elusive.
 
For the life of me, I just can't get streaming videos to play correctly over the web. Youtube works fine, but as far as Windows Media or Real Player streams go, it's a no no. 

(Also, I'm aware that Adobe Shockwave player doesn't have a Linux version as of yet- please, somebody tell me I'm wrong!!)

I've tried downloading all the plug-ins I could find and it just didn't work. The m-player plug-in was useless. Videos never loaded. VLC, which I swore by on XP, has let me down with streaming content from the net and Real Player just didn't seem to function at all. 

The Media Connectivity plug-in for for Firefox- sorry, I didn't mention that that's my browser- has facilitated things a little but Totem doesn't complete the streams and has serious sound and video issues.

Any suggestions would be GREATLY appreciated!!

---

### Post by qamelian on 2007-11-08
Not sure what to tell you regarding RealPlayer. If you have RealPlayer 10 installed and have run the application once so it can set up its browser helper, it should just work. It works flawlessly for me.

WIndows Media streams may be another thing altogether. Many WMV streams contain DRM which prevents them from being viewed in Linux media players.

Since you mentioned that mplayer plugin wasn't doing its job, I would assume that maybe you haven't installed the w32codecs that it needs in order to read many media types.

Check the Ubuntu wiki at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more info.

---

### Post by TWO on 2007-11-11
Once the codecs have been downloaded, does Mplayer have to be configured in a particular way? Also, is it a bad idea to have too many plugins for firefox??

---

### Post by atlascomplete on 2007-11-11
Try this thread right here:

[http://ubuntuforums.org/showthread.php?t=605837&highlight=flash+plugin](http://ubuntuforums.org/showthread.php?t=605837&highlight=flash+plugin)

---

### Post by TWO on 2007-11-12
I just installed Real Player and was reminded of the reason why had repeatedly removed it. It doesn't start up!! Has anybody else experienced this problem??

---

### Post by philinux on 2007-11-12
This may help ..

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by comfortablynumb on 2007-11-12
I been having the same problem, no matter the plugin there are still sites that won't stream. One off the top of my head is the Atlanta Panda Cam [http://www.zooatlanta.org/animals_panda_cam.php4](http://www.zooatlanta.org/animals_panda_cam.php4) I've tried all the media players Mplayer, Totem both Gstreamer and Xine, Vlc, Firefox media plugin.

---

### Post by TWO on 2007-11-20
> **philinux said:**
> This may help ..

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I have all the codecs mentioned on that help page and am quite certain I have come across that page or at least something similar before. 

I don't know about you, but VLC media player doesn't seem to work as well on Ubuntu as it does in Windows- I hate to admit.

You'd think that with all the codecs, playing media wouldn't be a problem. I just received an update for mplayer today however so I'll see if that makes any improvements. 

Is there anyone out there whose online media plays flawlessly??? :confused::confused::confused:

---

