---
title: "Totem + divx 5"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-10-31
I get this message when I try to play some divx movies:

> Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies

I have every plugin that I know of installed. Any ideas?

---

### Post by RomeReactor on 2007-10-31
Hi. Most likely you're missing some libraries; try searching for **ubuntu-restricted-extras** in Add/Remove or Synaptic, or to install from the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by arijarot on 2007-10-31
> **RomeReactor said:**
> Hi. Most likely you're missing some libraries; try searching for **ubuntu-restricted-extras** in Add/Remove or Synaptic, or to install from the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

I looked at the package -- I already have libxine1-ffmpeg installed.

Edit: I made a mistake. I only had libxine1 and not libxine1-ffmpeg. installed libxine1-ffmpeg and now it works. thanks, RomeReactor!

---

