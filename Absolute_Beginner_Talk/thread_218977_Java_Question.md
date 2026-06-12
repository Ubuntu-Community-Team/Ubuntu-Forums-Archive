---
title: "Java Question?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by darkwoofe on 2006-07-19
I've installed Sun Java 5.0 Runtime via the repository along with the plugin for Firefox and that seems to be working fine. The problem is that I don't Sun Java is being used as the default for anything else.

How would I set Sun Java 5.0 Runtime as the default and do I need to uninstall the Java that came with the instillation of Ubuntu? 
If I do need to remove it, which packages do I remove?

If someone could help me out, I'd be very thankful.

---

### Post by thoolihan on 2006-07-19
```
sudo update-alternatives --config java
```

This is covered in the desktop guide:
[http://help.ubuntu.com/ubuntu/desktopguide/C/](http://help.ubuntu.com/ubuntu/desktopguide/C/)

specifically at:
[http://help.ubuntu.com/ubuntu/desktopguide/C/programming.html](http://help.ubuntu.com/ubuntu/desktopguide/C/programming.html)

Best of Luck,
-Tim

---

