---
title: "GStream error"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Psychobiker on 2007-08-11
In Totem movie player - even with the codecs installed, I get a GStream error, and the file just won't open. Any ideas what's causing this, and how else can I play a .mov file?

L

---

### Post by bren on 2007-08-11
did you try this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins)

---

### Post by ajgreeny on 2007-08-11
I was going to suggest you install totem-xine instead of totem-gstreamer, but I see this is part of the info already given above.  It seems to work much better than the gstreamer version, in my opinion.

---

### Post by Psychobiker on 2007-08-13
OK, just installed totem-xine. It opens the file and plays from 19 mins to 25 mins about 8x as fast as it's meant to! No video or sound. No prompts for codecs eitehr

L

---

### Post by jspangler on 2007-08-13
With totem-xine, you can download all the codecs you need through Synaptic by installing the codecs from the medibuntu repositories: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

and then installing ffmpeg and/or w32codecs. This should work with the following commands:

```
sudo apt-get update
sudo apt-get install ffmpeg w32codecs
```

I think that should get you mostly up and running.

---

### Post by jspangler on 2007-08-13
You also might want to install the package libdvdcss.

---

### Post by Psychobiker on 2007-08-13
cheers, will try!

L

---

### Post by Psychobiker on 2007-08-13
same thing happens even after codecs - plays thefile very fast with no video

L

---

### Post by jspangler on 2007-08-13
Try the following command:

```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

and see what happens.

---

### Post by Psychobiker on 2007-08-13
all the latest versions installed, I'm afraid

L

---

### Post by jspangler on 2007-08-13
Hmm, I'm all out of ideas... This stuff always worked for me before. Good luck.

---

