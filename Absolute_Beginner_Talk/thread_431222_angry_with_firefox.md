---
title: "angry with firefox"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-05-02
I have always used firefox even on my windows box and loved it. but now i am having a problem.

I am not sure if it is firefox or mplayer, but every time i try to close a window that is playing a video firefox freezes. does anyone know a fix. or what my problem is?

---

### Post by Vajra Vrtti on 2007-05-02
If you use many Firefox extensions the first thing to do is to start Firefox in safe-mode to check if any of them is causing the problem. Sometimes extensions can cause weird problems, completely unrelated to their function.

---

### Post by starcraft.man on 2007-05-02
> **alexlex said:**
> I have always used firefox even on my windows box and loved it. but now i am having a problem.

I am not sure if it is firefox or mplayer, but every time i try to close a window that is playing a video firefox freezes. does anyone know a fix. or what my problem is?

[https://addons.mozilla.org/en-US/firefox/addon/446]("https://addons.mozilla.org/en-US/firefox/addon/446")

Install that addon, then when you set it up, default everything to totem player (also make sure you have all your codecs). It makes streaming video very easy and it will play in a seperate window, should prevent you from crashing too. Highly recommended plugin.

---

### Post by alexlex on 2007-05-02
bump

---

### Post by starcraft.man on 2007-05-02
Did you try the addon I supplied? It shunts your streams out of firefox and launches the player seperately, thereby, can't crash firefox I don't think >.>. Hope my logic isn't faulty...

---

### Post by kerry_s on 2007-05-02
> **starcraft.man said:**
> [https://addons.mozilla.org/en-US/firefox/addon/446]("https://addons.mozilla.org/en-US/firefox/addon/446")

Install that addon, then when you set it up, default everything to totem player (also make sure you have all your codecs). It makes streaming video very easy and it will play in a seperate window, should prevent you from crashing too. Highly recommended plugin.


I also reccomend the media player plugin, it really helps to seperate the media from the browser.
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by alexlex on 2007-05-02
> **starcraft.man said:**
> Did you try the addon I supplied? It shunts your streams out of firefox and launches the player seperately, thereby, can't crash firefox I don't think >.>. Hope my logic isn't faulty...

i did try step be step but it failed to work for some reason the video still opened in firefox

---

### Post by starcraft.man on 2007-05-02
> **alexlex said:**
> i did try step be step but it failed to work for some reason the video still opened in firefox

Go to tools menu in firefox, select media player connectivity, select configure. A dialog should pop up, do all of the ticked off formats say:

```
/usr/bin/totem
```

If they don't all say that, paste it into the space where you can type text next to the format.

If they all do say totem, please type out which formats are ticked...

---

### Post by alexlex on 2007-05-03
> **starcraft.man said:**
> Go to tools menu in firefox, select media player connectivity, select configure. A dialog should pop up, do all of the ticked off formats say:

```
/usr/bin/totem
```

If they don't all say that, paste it into the space where you can type text next to the format.

If they all do say totem, please type out which formats are ticked...

they all say /usr/bin/x11/gmplayer/

---

