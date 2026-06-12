---
title: "Finding out version numbers (ATI / gstreamer)"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by hapveg on 2008-02-13
Question first, then the background info:

How do I find out which version of the ATI drivers I'm using, and whether totem is using gstreamer or another decoder, and anything else related to video display.

Background:
I've been using ubuntu for a month, and while I got totem to play movies within 5 minutes, they'd be noticeably pixelated. VLC was the same. "sudo aticonfig --ovt Xv" worked for some people, but not me. After a few weeks of editing xorg.conf / messing with drivers / compiz / anti-aliasing / just about everything I could find, it worked, almost flawless video playback (slight tearing, but otherwise perfect).

Now I've installed Ubuntu onto a larger harddrive, I've copied xorg.conf, and run "sudo aticonfig --ovt Xv", but my new ubuntu is still getting pixelated video.

I've still got me older ubuntu, and I'm hoping to find out what settings I actually changed to get it working, and do the same with my new install.

I'm running an ATI X1900XTX on a widescreen 1680x1050 monitor, and I've noticed that ATI drivers tend to mention various problems with that resolution in their 'Known Issues', and from the [release notes of the latest drivers](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_82_linux.html):
"Video playback may look blocky when playing a video file using a video player that utilizes the XVideo extension"

I'm guessing either my old install was using a different driver, or I'd somehow enabled fullscreen anti-aliasing, or some compiz tweak magically fixed it.

Anyone have any thoughts, or can someone tell me how to find out which driver version I am using / gstreamer / xine version.

---

### Post by jan quark on 2008-02-14
for finding the version run this
```

glxgears -info
```

---

