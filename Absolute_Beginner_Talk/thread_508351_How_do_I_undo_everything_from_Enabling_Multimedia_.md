---
title: "How do I undo everything from: Enabling Multimedia in Feisty (HOW-TO)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-24
How do I undo everything from: **Enabling Multimedia in Feisty (HOW-TO)** turorial?
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I've done some tinkering on xorg.conf file when trying to configure my monitor, but experimenting on that file has resulted in all media codecs not function as normal after having followed the tutorial.  So now I want to uninstall every codec from that tutorial and install fresh to see if that will fix things.

So far I only managed to remove **For DVD Playback and Win32 Codecs ** by doing this.
```
sudo apt-get --purge remove libdvdcss2 w32codecs
```
But I'm having trouble uninstalling these

    * "GStreamer ffmpeg video plugin"
    * "GStreamer extra plugins"
    * "GStreamer plugins for aac, xvid, mpeg2, faad"
    * "GStreamer plugins for mms, wavpack, quicktime, musepack"

    * "Ubuntu restricted extras"
    * "Macromedia Flash plugin"

using Add/Remove trying to uninstall instead it suggest me to use Synaptic to uninstall.
But when searching for Macromedia I don't see any already checked row to uncheck.
Help plz?

---

### Post by jingo811 on 2007-07-24
Never mind I figured out how to use Add/Remove and Synaptic to co-operate and pinpoint the programs I'm looking for.

---

