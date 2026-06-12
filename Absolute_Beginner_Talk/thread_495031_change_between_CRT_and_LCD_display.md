---
title: "change between CRT and LCD display"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Shun_di on 2007-07-07
Hi guys,

I have recently enabled desktop effects for my system and it required installing new nvidia (nvidia4 420 go) drivers for my laptop, which it did automatically. when i restarted it came up with a black screen. I found that the laptop is displaying on to a external monitor, but none is connected. When i do connect a monitor to it i can use the external monitor fine. What i want to know is how do i switch back to my LCD screen on my laptop. I am a complete noob at ubuntu so could someone give a step by step guide how to switch between LCD and CRT.

Oh by the way i have tried pressing Fn+F5 on my Toshiba laptop but that doesn't work.

Thanks in advance.

---

### Post by annda on 2007-07-07
plug in the monitor and run nvidia-settings as root. if you can't find it in your menus, run it from the terminal.

```
gksudo nvidia-settings
```

disable the external monitor and enable the panel. write changes to xorg.conf before quitting!

restart x and you should be fine. (CTRL+ALT+BACKSPACE)

---

