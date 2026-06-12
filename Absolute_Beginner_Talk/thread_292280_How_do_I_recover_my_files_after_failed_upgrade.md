---
title: "How do I recover my files after failed upgrade?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2006-11-03
I tried to upgrade to Edgy Eft an got some Xorg desktop error, that meant I couldn't login to the graphical enviroment. So I've burnt a copy of Edgy Eft and am hoping to recover my files via live CD and then do a fresh install.

How can I do this as the drives aren't mounted?

---

### Post by taurus on 2006-11-03
Have you tried to reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Fully216 on 2006-11-03
If you have a backup of your xorg.conf, you can always revert to that via the cli (which is what I had to do when I tried to upgrade).

---

