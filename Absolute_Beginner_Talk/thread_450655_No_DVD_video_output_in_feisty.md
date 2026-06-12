---
title: "No DVD video output in feisty"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by lsalminen on 2007-05-21
Hi,

I've tried the sticky here, as well as the HOWTO guide, but all I get is sound output in VLC and Movie Player. I can hear everything, but there is no video on screen. Am I missing a codec or something? 

I have installed:

 GStreamer extra plugins
 Gstreamer ffmpeg video plugin
 GStreamer plugins for aac, xvid, mpeg2, faad
 GStreamer plugins for mms, wavpack, quicktime, musepack


Thanks,
Lee

---

### Post by rich.bradshaw on 2007-05-21
libcss2

---

### Post by lsalminen on 2007-05-21
Hi,

Ya I already have libdvdcss2 installed via terminal, and I've uninstalled and re-installed all of those plugins.

Any other ideas?

---

### Post by thunderkyss on 2007-05-21
go into your package manager, search for 

libxine1-ffmpeg

mark it for installation, apply changes

watch DVDs

---

### Post by lsalminen on 2007-05-22
That was already installed. 

What player should I use to watch DVD's? I have a ton installed. The one I've been trying to use is:

Totem Movie Player 2.18.1 with Movie Player using xine-lib version 1.1.4 and GNOME.

When I try to watch a DVD, all that appears is a blue screen.

Thanks, Lee

---

### Post by jsenner on 2007-06-09
I have the same problem. It's a problem with the interaction between any video players and your video or graphics driver. I am using the Intel video driver with these results. The videos play if I use Vesa driver instead of the proper Intel driver, but Vesa is too slow and frame rates go way down.

Anyone have a fix?

Jeremiah

---

