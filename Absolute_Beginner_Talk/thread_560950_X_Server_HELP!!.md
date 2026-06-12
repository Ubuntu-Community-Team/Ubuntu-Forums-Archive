---
title: "X Server HELP?!?!"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Cherio on 2007-09-27
MY Computer is telling me that my xserver is not installed.

When i plug in my card it boot like its going to start then gives me an error saying 0 screens found and that my xserver is not congigured properly and that it will shut down untill reconfigured but then im stuck at a screen like the termanal and can get to my desktop.

than i unplug the card so i can actually get to the desktop and try to configure it and i just get xserver not found.

Please help?

---

### Post by startherepodcast on 2007-09-27
Try Entering:

```
dpkg-reconfigure xserver-xorg
```

to reconfigure you xserver.

---

