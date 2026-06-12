---
title: "Control Volume in XFCE"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-04-10
How can I control my volume in XFCE ? I looked for a plugin but I couldn't find anything.

Edit: There should be a Misc DE support section. Can I request this somewhere ?

---

### Post by aysiu on 2006-04-10
```
sudo apt-get install xfce4-mixer
``` ?

---

### Post by Thiago on 2006-04-11
go to xfce panel control, add a new item -> volume control -> properties -> select your device (/dev/mixer) -> finito :)
ah... you can change whatever you want to control (vol, pcm, phoneln...) just go to "wannabe master" (volume control properties)

---

