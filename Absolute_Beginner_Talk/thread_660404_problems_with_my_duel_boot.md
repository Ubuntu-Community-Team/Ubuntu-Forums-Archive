---
title: "problems with my duel boot"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by phoenix5211 on 2008-01-06
I have my duel boot set up. I can boot into either windows xp or ubuntu. The problem is when I switch back to ubuntu I have no sound, and my nvidia driver is not working properly. It switches to low graphics mode. I am running the latest video driver. Any help would be greatly appreciated

---

### Post by Toxicity999 on 2008-01-06
Can you post the output of /var/log/Xorg.0.log ?
cat /var/log/Xorg.0.log

---

### Post by phoenix5211 on 2008-01-06
I just fixed the video problem by removing the new video driver and dropping back to the older restricted driver, then locking the version. hope the attachment is the one you asked for. am still very new to all of this

---

