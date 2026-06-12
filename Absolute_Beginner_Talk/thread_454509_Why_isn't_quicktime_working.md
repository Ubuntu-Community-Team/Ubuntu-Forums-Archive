---
title: "Why isn't quicktime working?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-05-25
So I downloaded and installed Quicktime, since Totem doesn't play a lot of videos. After I installed it however, I went to play a video and I got the same message that Totem could not do whatever it is that Totem needs to do in order to play a video. But I have Quicktime and this was recommended for the file I was trying to access. So why didn't this solve it. I did restart my puter... I did the whatchamacallit from the command line successfully...

---

### Post by starcraft.man on 2007-05-25
Totem plays every format I have ever thrown at it. You simply need to install the right codecs. Follow [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") and paste the command in, also make sure to install win32 codecs. 

Also, if you want a universal player with no effort, you want VLC not quicktime, it will play anything out of box (except maybe RM files).

```
sudo aptitude install vlc
```

That should be it, don't use quicktime in wine though, I don't see why one should support a DRM company on linux >.>.

---

### Post by Aurora Borealis on 2007-05-25
Awesome-thank you very much. 

I'd be happy to hear more on the DRM company situation-fill me in, if you'd like.

---

