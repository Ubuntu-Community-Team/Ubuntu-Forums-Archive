---
title: "Downloaded ATI Driver"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-01-02
Just downloaded the newest ATI driver (mainly because Im tired of glrfx :P ) But since Im a newb  to linux am unsure how to run a .run file. Also how can I back up my system just in case this messes everything up? Thanks! :)

---

### Post by pay on 2007-01-02
Follow this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by happy-and-lost on 2007-01-02
Be ***very*** careful. The latest driver completely screwed my install up. Had to reinstall *sigh*

---

### Post by pay on 2007-01-02
Backup your xorg.conf before editnig it just incase something goes wrong```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```and if you need to revert the changes do```
sudo cp -r /etx/X11/xorg.conf_bak /etc/X11/xorg.conf
```

---

