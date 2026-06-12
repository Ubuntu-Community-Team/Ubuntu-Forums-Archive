---
title: "how do i find my videocard?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-16
i am trying to run a video on mplayer and keep getting a message saying "there is no Xvideo support for you card" and the drivers i am using dont work and to check for non vo x11 codecs.

how do i do that?

i also suspect this is the reason i cant view any type of video in vlc even tho in windows vlc works fine its very odd.

once i find my card are their drivers for it?

---

### Post by bluevoodoo1 on 2006-06-16
Well, you could try the following:

From a terminal: applications > accessories > terminal
```
lspci
``` look for something that refers to VGA compatible controller or the like. 

or

```
sudo lshw
```

---

### Post by maddbaron on 2006-06-16
ok thanks i entered them saw something say vga but no vendor named so i assume i dont have a card...thank you tho.

---

