---
title: "Too fast audio/video playback when using HDMI audio."
date: 2014-03-15
forum: Any Other OS
---

### Post by totson2 on 2014-03-15
After installing mint 16 yesterday I had no sound through HDMI and all audio/video was playing too fast.  
After googling around a bit I found that AMD HDMI audio is disabled by default on 3.0+ kernels and I did the "radeon.audio=1" commandline on grub. This enabled the sound, but the playback was still at 4x.

 Some additional info: when I change my output device to something other than HDMI it works fine, and when I change the resolution to something other than native(1920x1080), the audio and video works fine through HDMI. 
Before mint I was using ubuntu 13.10 and never had the fast playback problem, after doing the "radeon.audio=1" trick to enable the sound it worked fine.

My card is the HD4870 and I'm using the open source driver, since the proprietary is abandoned as far as I know. I have found that many people have the same problem, but no solution other than to wait for an update to the driver.

---

### Post by howefield on 2014-03-15
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by tgalati4 on 2014-03-15
That's an excellent description as to why HDMI sound was disabled.  If you play the video in VLC, look in the message window (turn up the debug level) and see what errors are posted.  As you have already figured out:   Use the proprietary driver (on the latest distro that supports it) or wait for the open driver to be patched.  Have you found a bug tracker for this problem against the open video driver?

Play a known frequency (Say A key, 440 Hz) and use your smartphone with a tuner app and see if it is exactly 4X or just near 4X.  It could be the difference between 20 kHz-encoded audio verus 96 kHz digital super audio when in 1080 mode.

---

