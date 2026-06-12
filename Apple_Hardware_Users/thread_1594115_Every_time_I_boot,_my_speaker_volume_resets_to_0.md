---
title: "Every time I boot, my speaker volume resets to 0"
date: 2010-10-12
forum: Apple Hardware Users
---

### Post by jamesey on 2010-10-12
I'm on 10.10
Everytime I start my iMac, the volume in alsamixer is reset to zero. It takes 8 seconds to fix, but I'd rather not have to do this every time I boot up. Anyone know how to fix this?

screenshot attatched.

---

### Post by linuxopjemac on 2010-10-12
After you make your alsamixer changes, you have to save settings by running 
```
alsactl store
```

---

