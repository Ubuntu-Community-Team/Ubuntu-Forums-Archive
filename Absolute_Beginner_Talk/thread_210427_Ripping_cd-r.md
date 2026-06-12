---
title: "Ripping cd-r"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2006-07-06
What is a good program for ripping "home made" cd's that will identifythe name of the song and stuff. I know iTunes does this, but that is only for mac and windows. Is there another program that can do this? Most of the songs I'm doing are pretty popular if that makes a difference.

---

### Post by Jagot on 2006-07-06
Sound Juicer which is already included in the default install:

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by milehigh on 2006-07-06
Soundjuicer.

---

### Post by acorn22 on 2006-07-07
Do I need to get LAME then? Or am I good to go?

---

### Post by Jagot on 2006-07-07
Assuming you're using Dapper:

```
sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-ugly-multiverse
```

As explained in the wiki in my link above.

---

