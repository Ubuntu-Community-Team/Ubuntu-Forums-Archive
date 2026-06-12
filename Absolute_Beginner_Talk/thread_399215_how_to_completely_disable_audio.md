---
title: "how to completely disable audio?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by HighD on 2007-04-02
Ok, so I just got my Ubuntu 6.10 Server running :) . When it starts up, it gives me some errors messages regarding ac97 like **"ac97 codec read timeout" **or **"ac97 access error" **and stuff like this. 

I don't need sound from my server so...is there anyway I can **completely disable the sound** so the computer can **skip this whole audio recognition**??

Thanks in advance for all your answers :-D

---

### Post by Gen2ly on 2007-04-02
Nooooooo Problem.  Look in Synaptics and uninstall everything that has alsa, oss, and esd.

---

### Post by HighD on 2007-04-02
Ok, is  there any EASY way I can do this from the terminal??

---

### Post by rubinstein on 2007-04-02
You could also try to disable the sound in your BIOS, if it is an internal sound chip on your motherboard. This I think is the easiest way.

---

### Post by HighD on 2007-04-02
> **rubinstein said:**
> You could also try to disable the sound in your BIOS, if it is an internal sound chip on your motherboard. This I think is the easiest way.

Just what I did rubinstein. Worked great, no more errors, thanks! :D

---

