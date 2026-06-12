---
title: "Playing m4a"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-02-07
Ok i am a newbie \\:D/ and am trying to figure out how to play my m4a that i have form itunes on ubuntu without first having to change them to mp3. any suggestions

Shade

---

### Post by kaamos on 2006-02-07
Hello!

This should help
1. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
2. Applications->Accessories->Terminal
```
sudo apt-get install gstreamer0.8-plugins-multiverse bmp-mp4 xmms-mp4
```

---

### Post by HokeyFry on 2006-02-07
just open synaptic and install the gstreamer package that installs all of the sound plugins. I can't tell you the exact name of it because I am using a windows computer right now, but I know the first word is "gstreamer". just search for "gstreamer" in synaptic and if you choose the correct one it will install all of the sound plugins you will need.

---

### Post by shickidyshade on 2006-02-08
is there a seperate program the gstreamer works with or is there only one

---

