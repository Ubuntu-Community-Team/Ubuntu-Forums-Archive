---
title: "no sound no video"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by skippy51 on 2007-03-02
hi,i have now 6.10,bud i can not listen to radio stations on the internet,(fmradio.nl)
also i cannot see video,s.
withe 6.06 was that not a problem
gegards skippy the netherlands

---

### Post by carlosfocker on 2007-03-03
Does the sound work on any applications?

When you say you cannot see videos does that mean there is sound but no video or that the video just doesn't play?

If it just doesn't play then try loading some codecs.  This following line will load pretty much all the codecs you will need for video play back.
```

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

---

