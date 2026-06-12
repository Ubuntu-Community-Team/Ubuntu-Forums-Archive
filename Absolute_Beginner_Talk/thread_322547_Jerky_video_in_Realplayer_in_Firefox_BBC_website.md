---
title: "Jerky video in Realplayer in Firefox BBC website"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2006-12-20
I'm so impressed with Ubuntu, I've now installed it (6.10) on my laptop in place of Windoze. Everything works except for Realplayer video in the BBC News website. It does work, but, unlike on my desktop, the video is jerky (sound is OK) and the response (eg to stop playback) is sluggish.

I've trawled through the forums looking for this subject and either a thread has gone unanswered, or the answer is far too technical for an Ubuntu beginner like me. Can anybody point me *in simple terms* in the right direction, please? My laptop is only a few months old and plays film trailers in Gxine perfectly (and full screen too!), so I don't think that it's a hardware problem.

Thanks!

---

### Post by schwascore on 2006-12-21
I never had much luck with Helix or RealPlayer as a browser plugin.  Why not try the VLC browser plugin?  I just switched to it from mplayer and everything runs a lot smoother.

---

### Post by Charlie Chick on 2006-12-24
After much experimenting I cured this problem by installing Gstreamer 0.8plugins, which Synaptic says is "all Gstreamer plugins". Now the video works without jerking.

---

