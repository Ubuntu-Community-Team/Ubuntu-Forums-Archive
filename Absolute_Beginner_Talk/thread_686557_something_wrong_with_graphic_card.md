---
title: "something wrong with graphic card"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by lapor on 2008-02-03
I have one problem. my Ubuntu 7.10 doesnt go to desktop. it stops. it says that there is something wrong with my graphic card. I tried to modified file /etc/X11/xorg.conf (when I was instaling drivers for ati radeon 9200se with [https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)  )
Last I did was typed sudo /etc/init.d/gdm restart in text console. And now I cant get to desktop. I stuk in text console.

help

---

### Post by taurus on 2008-02-03
Reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by lapor on 2008-02-03
tanks.
I manage to get to desktop. but what to do now?
I checked /etc/X11/xorg.conf and it is the same as it was before I change it. (I supose its backup). but I cant shut down the sysetm.

---

