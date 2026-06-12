---
title: "Where is the Totem Codecs directory?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Zoggy888 on 2008-03-18
I recently installed Gutsy desktop on a P3 and an, s Acer Aspire laptop.  The installs went smoothly with some help from a few forum threads and googling.  The only problem is, I can play Real Media file .rmvb in Totem using GStreamer on the P3,  but on the laptop, Totem using GStreamer:confused:, It plays the audio, but not video.   I want to compare the setting on the P3 and laptop to find the difference,  but I don't know where to look.  Can someone tells me where the Totem Codecs Directory is, Or where the config file if any.   By the way, I copied the files from /usr/lib/win32 to /usr/lib/codecs, still the laptop Totem would not play the real media file.

---

### Post by Hospadar on 2008-03-18
what you should do, is go into synaptic, search by name for gstreamer, pick one of the codec packages (any one that's installed, it doesn't really matter which) right-click->Properties->Installed Files, look for library files.  If you see files in "doc" or "man" directories those are probably not it.

Also, you should probably copy those files you copied back to their original location.

The problem may well be with your sound hardware and not gstreamer or real.  You may want to try using xine instead of gstreamer (install the "totem-xine" package

---

### Post by Zoggy888 on 2008-03-19
Looks like I was missing some components from the Restricted Format repository, which is kinda strange, as I can play the Real Media file in Mplayer.  I reinstall the restricted format:

sudo apt-get install ubuntu-restricted-extras

then re-install these packages:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Now, I can play Real Media file in Totem using GStreamer.

---

