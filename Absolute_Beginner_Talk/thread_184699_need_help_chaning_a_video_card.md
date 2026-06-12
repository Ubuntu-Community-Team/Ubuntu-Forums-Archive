---
title: "need help chaning a video card"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by mayonesiac on 2006-05-30
so i installed ubuntu on my second pc (p4 1.4 ghz) and decided that i should probably change the video card from geforce2 mmx 4400 to g5 fx5500. so i simply shutdown my pc, changed the video card, triple checked everything and booted up ubuntu, which ofcourse crashed in minutes. i am perfectly sure the fx5500 is working fine, so i realised there must be something i have to do before switching video cards. can anyone help me?

---

### Post by bruce89 on 2006-05-30
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by frodon on 2006-05-30
run a : ```
sudo dpkg-reconfigure xserver-xorg
```Then re-install your nvidia drivers and it should be good, don't hesitate to ask if you need assistance.

---

### Post by mayonesiac on 2006-05-30
thank you so much, i entered the line in recovery mode, pressed enter a bunch of times and now it seems to be working fine.

---

