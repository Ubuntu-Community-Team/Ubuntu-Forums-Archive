---
title: "My media player picture quality is so bad..."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-14
Hello, I have been messing around with VLC and Xine media players.

My problem is that the playback picture quality for wmv files is really poor compared to the way the same exact videos played on WMP10.

This is my internal graphics card: Intel Graphics Media Accelerator 900

I have added these codecs:

gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs 
ffmpeg 
lame 
faad 
sox 
mjpegtools 
libxine-main1

and these multimedia codecs: 

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs


as well as all of the libraries suggested by VLC when I installed with this code: sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc

 The following extra packages will be installed:
  libggi2 libgii0 libgii0-target-x libglide2 libsvga1 vlc-plugin-arts
  vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl
  vlc-plugin-svgalib
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 device3dfx-module
  device3dfx-source
Recommended packages:
  libggi-target-x libggi-target glide2-bin

plus, when I installed the recommended packages and the suggested packages, I followed instructions in the terminal when suggested or recommended to add certain packages and libraries for virtual3d. (I hope that was safe)

...I mostly just want the exact (or better) picture quality for wmv files that I had using WMP10.

any helpful hints would be cool,
thanks,
-c.

---

### Post by Sef on 2006-10-14
> ..I mostly just want the exact (or better) picture quality for wmv files that I had using WMP10.


Do those files have a DRM on them? If so, then they won't show well.

---

### Post by crimesaucer on 2006-10-14
does video playback quality differ on xubuntu/ubunutu from Windows Xp.

I'm sure there is a way to make it look as good or better then wmv played in WMP10.

if you know of a tutorial or link that helps, please post the link.

thanks.

---

### Post by crimesaucer on 2006-10-14
No. the media files are just simple trailers from different websites that I was viewing from, to test my VLC and Xine, I haven't even tried my DVDs and CD movies. I also downloaded a few trailers from a few sites to test how they played as saved wmv files.

Everything works and plays perfectly with the Xine. But my problem with Xine is the picture is really poor and the look is not to my liking, but maybe I could install a different front end theme if I can fix the picture first.

But more importantly, the picture is really bad and the only adjustments were contrast and brightness, which only improved the picture a bit.

I also tested video from various sites and downloads with VLC which only played some videos off some sites and errored with others. Downloaded video didn't play at all. For what did play on VLC, was the same "bad" quality picture as Xine, all though, the settings and preferences on VLC seemed like I might be able to really adjust things to make it better if I knew what to do.

---

### Post by crimesaucer on 2006-10-14
has anyone had a poor picture quality on their VLC and Xine as compared to WMP10?

---

### Post by robert114 on 2006-10-26
I do, only in the dark collors and this problem did only occor in edgy!

---

