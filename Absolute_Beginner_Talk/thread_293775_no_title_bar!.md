---
title: "no title bar!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by djcawthorne on 2006-11-05
hi all,

every application i got on has no title bar! :( proving very difficult to use!

any advice most welcome.

---

### Post by Kateikyoushi on 2006-11-05
I would check the System >> Preferences >> Themes.

---

### Post by djcawthorne on 2006-11-05
checked, all seems fine. any other ideas?

---

### Post by Kateikyoushi on 2006-11-05
I see you installed XGL did you install beryl or compiz ?
If so xgl might not be loaded, check your /etx/X11/xorg.conf or this should add it.
```
sudo nvidia-xconfig[CODE]


This is what I did, if you use the nvidia glx driver.
[CODE]dpkg-reconfigure nvidia-glx
```

---

