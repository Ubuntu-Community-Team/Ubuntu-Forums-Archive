---
title: "Screen Resolution Problems"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-05-07
Just installed Feisty on a HP zt1000 laptop.

Everythign works except the screen resolution. Right now it is set at 1280x1024 and looks and works great.

However, I prefer a slightly lower resolution, but when I switch to any resolution lower than 1280x1024, then the picture doesn't fill the entire screen - almost like its not being "scaled up" to the laptop monitors native pixel resolution.

I there any way I can get all resolutions to fill the entire screen as it should??

Thanks

---

### Post by fakie_flip on 2007-05-07
sudo dpkg-reconfigure -phigh xserver-xorg

Then push control alt backspace.

---

### Post by John.Michael.Kane on 2007-05-07
If your still having issue.You can the method outlined here.
[http://ubuntuforums.org/showthread.php?p=2605716#post2605716](http://ubuntuforums.org/showthread.php?p=2605716#post2605716)

---

### Post by jondecker76 on 2007-05-07
thanks, i will try these

---

### Post by fakie_flip on 2007-05-07
Did you get it fixed?

---

### Post by fakie_flip on 2007-05-11
Did you?

---

### Post by jondecker76 on 2007-05-11
No, no dice..  
I tried a few different drivers (vesa, savage, S3) and all with the same problem -  so i'm just stuck running in 1400x1050 resolution because that is what fills my entire screen. I've enlarged the fonts a little and it seems to help, but thats all I can come up with

---

