---
title: "plugins?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by unawokendreamer on 2006-09-27
So I'm new to all this...


and all I really want to do is play music and movies,streaming or DVD. the programs tell me to get plugins, anyone know where I can get those?

Please and thanks

edward

---

### Post by pay on 2006-09-27
You need the right codecs.```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```should cover most of them (some of those may not be free codecs).

---

### Post by meborc on 2006-09-27
i strongly suggest you read the dapper guide (link in my sig)... for some of those codecs you need to enable extra repositories... how to do it read from there :) good luck

---

