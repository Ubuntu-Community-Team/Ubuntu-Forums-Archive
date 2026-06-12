---
title: "Missing codecs"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-19
Hi all, before you all point me very helpfully to ubuntu guide and the wiki etc, believe me I've already been there. I am using i386, I know about the issues with AMD64 and I have installed 32bit for the moment for ease of use. I used to be able to play .avi files no problems, and have installed the following (apologies if some are doubled up, I may accidentally put some twice)

gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

May I ask, why when I play .avi files, I get the sound but no video. I am running totem gstreamer, and have tried the xine but same problem, sound but no video... what am I doing wrong?

Thanks very much for your help,

Il

---

### Post by taurus on 2007-01-19
Have you tried using automatix2 to install all the codecs and plugins for the multimedia?

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by RomeReactor on 2007-01-19
Hmmm... though it's not likely to be missing, maybe you need to install libxine1:

```
sudo apt-get install libxine1
```

If it installs, try using totem-xine.

---

### Post by shareMenaPeace on 2007-01-19
Hello,
i can absolutly recommend automatix2 install for codecs, beside like 30 other well known and evolved tools like mediaplayer.

---

### Post by davebgimp on 2007-01-19
Sounds like you're missing the DivX codecs. I second the Automatix route, but you can also search the repos for 'divx' and look for the codecs package.

---

### Post by jvc26 on 2007-01-19
Hi guys, thanks once again for being advice legends, whatever the missing ones were, automatix2 installed them which is excellent :) All .avi are working now, thanks for your help,
Il

---

