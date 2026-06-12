---
title: "Can't see any video .ogg files."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Vadi on 2007-11-01
This is really odd, but I can't play any videos, not even .ogg files. I get sound, but no video - all players give me the same green screen.

I've already installed every possible gstreamer package I could find in synaptic, so I really don't know what else to get. I tried opening a random .ogg with mlayer, and here's what it told me:

```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88d1470]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 640 x 360 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 640x360 => 640x360 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================

```

Can anyone help? I find it baffling that I can't play the "open format" even anymore, argh :(

---

### Post by evilregis on 2007-11-01
I've had this happen to me too.  On my last install it happened.  I noticed it AFTER I installed ubuntu-restricted but I didn't notice WHEN it happened.

So I reinstalled (yesteday), just to see... I reinstalled.  Played the Nelson Mandela video.  Worked.  Installed ubuntu-restricted.  Played Nelson again.  Still worked.  Forgot about it until today... just tried it and got the same messed up video with perfect sound.

Hmmm... now as I typed this, I tried launching the video from terminal (totem ~/Examples/Experience\ ubuntu.ogg) to see if any errors would be output.  A player emerged, with sound and working video.

I don't know what's going on... I will try it again later and see what happens.

---

### Post by Vadi on 2007-11-02
I tried totem ~/Examples/Experience\ ubuntu.ogg, but it gave me a green screen as usual :(

---

