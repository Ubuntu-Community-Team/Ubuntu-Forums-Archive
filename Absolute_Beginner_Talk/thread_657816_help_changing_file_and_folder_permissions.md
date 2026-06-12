---
title: "help changing file and folder permissions"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by roddyguk on 2008-01-04
hi, this is prob a really easy issue to solve but i cant find it anywhere!!!

what im trying to do is change the owner and group permissions on a folder full of mp3s.

i change the folder by doing "chown rod.music MP3s/" which works fine but all the mp3s and other folders inside the mp3 folder are still owned by root and the group is plugdev!

please someone help, i dont wanna go through and do them all separately

---

### Post by cheahk on 2008-01-04
Try using the -R option for recursive:

```
chown -R rod.music MP3s/
```

Hope that helps.

-K

---

### Post by roddyguk on 2008-01-04
that worked perfectly thanks for your help

---

