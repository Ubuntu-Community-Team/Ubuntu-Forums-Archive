---
title: "wav to ogg (or even mp3) converter ?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-04-06
I have a huge number of wav music files, which needless to say, takes up a huge percentage of my harddrive space.

I would like to convert them to ogg (or mp3) to reduce this space.

Any suggestions ?

---

### Post by Ubuntuud on 2006-04-06
Huge numbers take a lot of time (I'm talking about hours and hours). To do this you could download sound converter from "add application" (not synaptic, it is there, but I don't know the name).

---

### Post by MartinG on 2006-04-06
The app in synaptic is called "soundconverter".  Or there's a script called audio-convert which you can get from:
[http://download.savannah.nongnu.org/releases/audio-convert/](http://download.savannah.nongnu.org/releases/audio-convert/)

EDIT:
Or, even simpler, open a terminal in the directory concerned and run```
oggenc *.wav
```

---

