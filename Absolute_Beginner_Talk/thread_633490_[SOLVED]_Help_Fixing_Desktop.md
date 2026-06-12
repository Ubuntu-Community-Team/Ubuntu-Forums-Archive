---
title: "[SOLVED] Help Fixing Desktop"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-06
Well I was messing with the screen saver and I tried making some changes and it ended up breaking my desktop back ground.This is the post I found that was supposed  to fix the screen saver.
[http://ubuntuforums.org/showthread.php?t=204582](http://ubuntuforums.org/showthread.php?t=204582)      Instead it broke my whole desktop background and all my shore cuts are gone and it will not let me change them or anything.

---

### Post by Crashmaxx on 2007-12-08
I'm not going to get into what went wrong here, but this should fix it:
```

sudo cp /usr/lib/libkdeinit_kdesktop.so.old /usr/lib/libkdeinit_kdesktop.so

```
And then restart X again.

---

### Post by jonward690 on 2007-12-08
Thanks man I already fixed it though but thanks anyways for the help

---

### Post by umattu on 2007-12-20
Could you post what you did to fix the problem?

---

