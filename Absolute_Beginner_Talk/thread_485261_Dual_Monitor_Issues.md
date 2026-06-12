---
title: "Dual Monitor Issues"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Djinn Effer on 2007-06-26
Hi. I'm using Ubuntu Fiesty Fawn 7.04, I have a nVidia GeForce 7800 GTx video card.

Alright, here's my problem: When I ctrl+alt+backspace and log back in, restart, etc, my other monitor is turned off. I have to go to terminal then nvidia-settings then X Server Display Configuration and set up the other monitor in twin view again. After that, I have to log out and log back in so my task bar at the bottom is only on my main monitor rather than stretching across both monitors.

I think perhaps the nvidia-settings aren't saving permanently for some reason? Also, does anyone know of a way to make the task bar stay on the main monitor without having to log out & log back in?

Anyways, if anyone can help I'd appreciate it.

---

### Post by bodhi.zazen on 2007-06-26
To save your changes run nvidia settings as root :

```
gksudo nvidia-settings
```

Then hit the save changes button.

For your panel, after you set your monitor it will sort itself out after 1 more log-out and in.

Or you can configure your panel ....

---

### Post by Djinn Effer on 2007-06-26
> **bodhi.zazen said:**
> To save your changes run nvidia settings as root :

```
gksudo nvidia-settings
```

Then hit the save changes button.

For your panel, after you set your monitor it will sort itself out after 1 more log-out and in.

Or you can configure your panel ....

That worked, thanks. Just had some strange issue with the minimize/maximize/restore buttons disappearing afterwords -- I'm using Beryl. But I easily fixed that: Advanced Beryl options -> Rendering path -> Copy. ^^

---

