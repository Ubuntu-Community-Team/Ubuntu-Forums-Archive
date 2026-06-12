---
title: "Oversized icons and text."
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by iguanaboy on 2008-01-29
Hello,

I posted this yesterday:

   Hello,

   and first of all, sorry if this has been asked before.

   I have just installed FF through Wubi, and everything is fine except for one thing: everything in Ubuntu is abnormally big. Text, icons, even my mouse cursor - everything. It makes Ubuntu very inconvenient to use.

   I don't know if that helps, but my video card is an old on-board Intel card.

   Many thanks to whoever can help


And I got some answers advising me to check my resolution settings in System, but that didn't work either. Any other advice?

Thanks.

---

### Post by bumanie on 2008-01-29
The most likely reason for the large text/icons is that the on-board video card has not been enabled. I have never used wubi, but as long as it is working OK, everything else should work the same. If you're using feisty fawn, have you gone into System --> Administration --> Restricted Drivers? I am not sure how well ubuntu supports intel, but go to restricted drivers and if there is a driver available for your on-board card, the restricted driver manger will download it. You may need to reboot after that to enable it properly.

---

### Post by erginemr on 2008-01-29
And if the above technique does not work, first copy your /etc/X11/xorg.conf file (which hosts the settings for the graphical server) with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```
and run:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
from a console.

---

### Post by barbedsaber on 2008-01-29
> **erginemr said:**
> 
from a console.

to open a console (more comenly known as a terminal, or command line) go to applications, accesories, terminal  I am not sure, but could this be a screen resolloution problem?

---

### Post by iguanaboy on 2008-01-29
Thanks a lot... I'll try all that.

---

