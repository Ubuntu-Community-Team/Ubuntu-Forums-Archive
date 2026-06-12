---
title: "Convert .flv to something"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-13
I've searched all over & still can't convert these files. Mac has such a sweet program called Visual Hub. I'm not smart enough to write it for Linux, but with all the brain power on this forum surely someone can match it! Or, is it & I haven't found i?

---

### Post by starcraft.man on 2007-05-13
Try this [site.]("http://media-convert.com/") It converts everything :D

---

### Post by Acglaphotis on 2007-05-13
Or you can try with ffmpeg

```
sudo aptitude install ffmpeg
```

Then you do 

```
 ffmpeg -i '/path/to/file.flv' -ab 56 -ar 22050 -b 500 -s 320x240 [name].avi
```

Its faster and you dont have to be online.

-Acgla

---

### Post by takuhii on 2007-06-28
FFMPeg is nice, but the resulting AVI's tend to be jerky...

---

### Post by Acglaphotis on 2007-06-28
I do it all the time and i get no problems with the resulting avis or whatsoever.

---

### Post by Cypher on 2007-06-28
> **takuhii said:**
> FFMPeg is nice, but the resulting AVI's tend to be jerky...

Not necessarily, it all depends on how you use FFMpeg. The proper arguments will yield a high-quality output. When I initially converted an AVI to FLV, it was very jerky and of bad quality. I then was told to do 2 passes and after learning a bit more about the tool, my FLV's are now of the same quality as the AVI, but considerably smaller..

---

### Post by hartz on 2007-06-29
> **Cypher said:**
> Not necessarily, it all depends on how you use FFMpeg. The proper arguments will yield a high-quality output. When I initially converted an AVI to FLV, it was very jerky and of bad quality. I then was told to do 2 passes and after learning a bit more about the tool, my FLV's are now of the same quality as the AVI, but considerably smaller..

Hey Cypher.

Would you be so kind as to post a howto on the subject!  It is a topic that I have had on the back-burner for a long time and have not yet had the time to invest into it.  So a howto would serve nicely to get me started and allow me to cheat on the initial learning curve :-)

---

