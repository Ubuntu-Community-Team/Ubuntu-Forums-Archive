---
title: "Is there any way to entirely remove and reinstall firefox?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-06-04
Well, I was doing some things with firefox, and it stopped working, so I tried uninstalling it and I think I might have made it worse. Now every time I try to install something I get this message.
"files list file for package `firefox' contains empty filename "
I tried uninstalling it in synaptic, but it gives me the same message. Is there any way to just remove any trace of firefox from my system and then reinstall it, or do I need to reinstall ubuntu?

---

### Post by bodhi.zazen on 2007-06-04
Yes

```
sudo apt-get --purge remove firefox
```

---

### Post by Romanus81 on 2007-06-04
I still get the same message, "files list file for package `firefox' contains empty filename "

---

