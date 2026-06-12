---
title: "[SOLVED] Reinstall"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2007-12-02
Hello all. I just migrated my drives to a different motherboard and CPU. Now X won't load on startup. Bunch of crap... fatal 10 error 104. I think what I need here is some command line input that will reinstall Ubuntu. My boot CD won't load X either, I suspect because it's too old to recognize my new hardware. I'll burn a new CD if I have to but I find that a pain. Any ideas? Thanks in advance.

---

### Post by Dr Small on 2007-12-02
Try running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by DrMilo on 2007-12-02
> **Dr Small said:**
> Try running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Perfect! Thank you!

---

### Post by Dr Small on 2007-12-02
No problem. Glad I could help :)
Please mark your thread as Solved from Thread Tools!

Thanks,
Dr Small

---

