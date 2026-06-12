---
title: "Update issues."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Harves on 2007-06-09
***I will first up start by saying that I am a complete Linux/Ubuntu newbie***

Upon turning on my system this morning I have found there are new updates. Upon clicking to accept the downloads I get the below error.

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I have also found when I go to add/remove I can no longer install applications.

Does anyone know how to fix this?

Cheers

---

### Post by AtrejuT on 2007-06-09
maybe you can try to do just what it says:
open up a terminal (from accesories - terminal) and type
```

sudo dpkg --configure -a

```

---

### Post by bapoumba on 2007-06-09
Please paste the output to:
```
cat /etc/apt/sources.list
```

---

