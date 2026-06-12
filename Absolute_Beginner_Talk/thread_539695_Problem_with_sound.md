---
title: "Problem with sound"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Reshuken on 2007-08-31
Hello everyone. Well, I have run into a problem with sound playback on my computer. I really don't know what could be happening, but the everytime my computer plays anything the sound comes out "distorted", like with a lot of noise (kind of when you mess up some equalizer settings).
Anyway, the strange thing is that I had encountered this problem before but it got away somehow (I don't know how, as I don't remember doing anything special), but a couple of days ago the problem returned.
By the way, I have a laptop, a Dell Latitude D600 with a Intel 82801DB-ICH4 sound card (I think)
Any kind of help is appreciated. Thanks!

---

### Post by Reshuken on 2007-08-31
Well I was able to find that it has something to do with PCM. I went to the terminal and typed "alsamixer" and after adjusting some levels here and there I found that the level of PCM is the one that "distorts" the sound when it's set to high. 
So, one solution could be to set it to a normal level, but what I don't like is that it puts a cap to the overall volume output of my system. Any other way I can work around this?

---

