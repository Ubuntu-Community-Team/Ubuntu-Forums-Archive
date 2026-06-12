---
title: "why ubuntu has gstreamer as default video playback framework?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-09-16
hello there

gstreamer is the default video backend.

By reading various posts & articles, it seems that xine is better than gstreamer. 

some + points of xine over gstreamer :

1. single plugin or file namely libxine-extracodec gives all most frequently used codecs, namely, divx, mpeg, mov , dat, vob, etc., unlike gstreamer which installs multiple files for different codecs.

2. Totem which is the default video player has ability to use xine as backend, so you don't need to install any video player in addition.

3. Better video quality. (at least i feel so)

4. Same xine works even in Kaffeine if you like to use Kubuntu later on.

5. Keyboard shortcuts are easier to use.

Then why does ubuntu uses gstreamer as default video playback despite the fact that Totem can easily use xine by totem-xine ?

---

### Post by DezSP on 2007-09-16
I think the main rationale is that gStreamer is basically designed for GNOME. For non-GNOME apps (like those in Kubuntu), clearly xine becomes much more useful, but gStreamer does a pretty good job for the vast majority of cases.

Also, on your first point, some might well consider having the codecs split up a feature rather than a flaw, it allows unneccesary codecs to be left out as needed.

---

