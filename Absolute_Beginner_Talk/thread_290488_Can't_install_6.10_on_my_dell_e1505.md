---
title: "Can't install 6.10 on my dell e1505"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by saltshaker on 2006-11-01
Ubuntu won't recognize the monitor and can't start the xserver.  Is there anyway I can install the damn thing in text mode and config the xserver options later?  Or should I just avoid this release and go with FC6?

---

### Post by llamakc on 2006-11-01
Is it a E176FP lcd monitor?

---

### Post by saltshaker on 2006-11-01
oops!  It's 1405.  It has 14.1 "trulife" WXGA+ wide LCD made by samsung

---

### Post by %hMa@?b&lt;C on 2006-11-01
try hitting ctrl+alt+f1 to switch to console. then type in
sudo dpkg-reconfigure xserver-xorg and thta should get your xserver working properly.

---

### Post by saltshaker on 2006-11-01
Thank you! Now it's working!

---

