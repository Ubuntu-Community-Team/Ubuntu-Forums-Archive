---
title: "&quot;Out of Range&quot; message after login"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by marenum on 2008-03-08
I recently tried to get my tv working as a second moniter using: [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

I never got that to work... but that's not important right now. I really screwed up my xorg.conf file and now after login i get a "out of range" message.

I'm a pretty new user, so I have no idea how to fix this.

---

### Post by PinkFloyd102489 on 2008-03-08
Means the resolution is probably too high for the TV or too low. Try changing the resolution.

---

### Post by marenum on 2008-03-08
Well, like I said, I'm pretty new to this. I can't do anything once the "out of range" message shows up. I can't see me desktop or anything. I'm not sure how I would go about changing my resolution...

---

### Post by Arthur Archnix on 2008-03-08
Try hitting Ctrl+Alt+F1 then login, then
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by marenum on 2008-03-08
I went through the reconfiguration process, a lot of which I was guessing on. One thing I knew for sure was my monitor's horizontal and vertical refresh rates. Still says out of range... Any more suggestions?

---

### Post by marenum on 2008-03-08
Perhaps somebody can help guide me through the reconfigure process???:confused:

---

