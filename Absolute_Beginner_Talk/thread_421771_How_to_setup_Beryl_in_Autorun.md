---
title: "How to setup Beryl in Autorun"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dorogavtsev on 2007-04-24
Hello, all!

Trying to setup Beryl in autostart:
ln -s `which beryl-manager` ~/.kde/Autostart
but it does not work.

When I'm writing the same thing again receiving the reply: File exists. But after reboot it doesn't work :-(

Thank you for your help :-)

---

### Post by tehbeermang on 2007-04-24
I just asked this question, but haven't tried it yet.

[http://ubuntuforums.org/showthread.php?t=421398](http://ubuntuforums.org/showthread.php?t=421398)

---

### Post by sisco311 on 2007-04-24
```
ln -s -T /usr/bin/beryl-manager ~/.kde/Autostart
```

---

### Post by dorogavtsev on 2007-04-24
Thank you! :-)

---

