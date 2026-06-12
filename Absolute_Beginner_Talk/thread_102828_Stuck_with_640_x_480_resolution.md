---
title: "Stuck with 640 x 480 resolution"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2005-12-12
I can't seem to select another resolution. Is this related to the fact I didn't get all the modules to load when I was installing Linux? (See my original Q: [http://www.ubuntuforums.org/showthread.php?t=102824](http://www.ubuntuforums.org/showthread.php?t=102824))

---

### Post by matthewv on 2005-12-12
So you used ubuntu after the install didn't finish totally?? It could be related if thats the case... Ask someone else: I don't know ;).

A ```
sudo dpkg-reconfigure xserver-xorg
``` might help...

---

### Post by johnnymo87 on 2005-12-12
thanks for the tip. I used the command to autodetect again, but no changes have occured.

---

### Post by Gustav on 2005-12-13
Look at [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by Mustard on 2005-12-13
I'd even suggest trying a 

```
sudo apt-get install ubuntu-desktop
```

and see if it installs anything that might have been missed in the original install.

Other than that I would be tempted to reinstall.

---

