---
title: "Ridiculous screen resolution problem...."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-15
I've just taken delivery of a gorgeous Dell 2007FP monitor (LCD flat panel). As you probably know, most LCD screens won't work above 60Hz refresh rate. They don't need to - because they don't suffer from the flickering problems that were common with phosphor dot CRT's.

So I duly reset my display settings to 60Hz and it works fine - as long as I'm logged in.

Unfortunately, the actual login screen itself is still working at a higher refresh rate (probably its old rate of 75Hz). Consequently, I can use Ubuntu - but I can't log into it...!

Is there any way to change either the resolution of the login screen or its refresh rate?

---

### Post by Ragazzo on 2006-12-15
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```

At the quite end you will be offered simple/medium/advanced options to adjust your monitor. Select medium (or advanced).

---

### Post by John E on 2006-12-16
Thanks - I tried that and it worked..! :D

---

