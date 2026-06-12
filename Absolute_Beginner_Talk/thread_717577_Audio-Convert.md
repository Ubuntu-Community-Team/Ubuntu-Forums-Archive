---
title: "Audio-Convert"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by marenkar on 2008-03-07
Hey I got this audio-convert script and it works well now, only one problem, only works for making it ogg or wav, how can i make it mp3?

---

### Post by kpkeerthi on 2008-03-07
Install **lame** from synaptic. You need universe and multiverse repos enabled.

---

### Post by marenkar on 2008-03-07
how do I enable universe and multiveres repos? Btw, which lame should I download? glame or toolame, Thats what I found in synaptic package manager, I use 6.06 LTS btw.

---

### Post by kpkeerthi on 2008-03-07
Goto System -> Admin -> Software Sources and enable the uni/multiverse repositories.
Then in a terminal type
```
sudo aptitude install lame
```

---

### Post by marenkar on 2008-03-07
Thanks!

---

### Post by kpkeerthi on 2008-03-07
I dont use audio-convert. It could be a bug or may be not or something that you should configure it not to create wav. I'll leave that to others to chime in.

---

