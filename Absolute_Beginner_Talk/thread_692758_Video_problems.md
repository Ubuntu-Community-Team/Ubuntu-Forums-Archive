---
title: "Video problems"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by raynorj on 2008-02-10
Hi,

I installed the "proprietary driver" for my Asus 9600 XT/TD when I was asked after I setup Ubuntu, two days ago. I didn't notice in the begining, but, at least now, movies play slow, frames alternate of the screen, even when I click the power off menu, that animation plays slowly, I can almost see it when it is drawing itself on the screen. What should I do about this? As recommended [here]("http://ubuntuforums.org/showthread.php?t=481691"), I changed the video output in GStreamer and VLC, but I doubt it has to do with this movie playing programs or their codecs.

I have Ubuntu 7.10, AMD Sempron 2600+, 512 RAM. Thanks.

---

### Post by ashmew2 on 2008-02-17
How did you Install your "Proprietary Drivers" ?

---

### Post by Hobo Joe on 2008-02-17
Paste the output of the command:
```

glxinfo

```

That will tell us what card you have(if it's detected properly) and the drivers it's using, as well as lots of other useful information.

---

