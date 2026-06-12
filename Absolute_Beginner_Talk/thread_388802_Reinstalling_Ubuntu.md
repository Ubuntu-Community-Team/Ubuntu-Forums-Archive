---
title: "Reinstalling Ubuntu"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by RodneyW on 2007-03-19
Is there a way to reinstall Ubuntu and keep all my files (d/l progs etc) without it wiping the disk and starting from scratch. My problem is I updated Nvidia drivers and now I get a totally black screen when it tries to start. I had a post about this but no-one seems to know how to fix this. Ive already spent about 6 hrs trying to get back into ubuntu with no luck and by the time I spend another six hours I could reformat and start from scratch by then. If this happens again however Ill just give Ubuntu a miss as this seems ridiculous.

---

### Post by CSandman on 2007-03-20
Try booting into the recovery shell.  From that you should be able to use apt-get to remove the problematic nvidia drivers.  After that and a reboot you should be good to go!

---

### Post by zvacet on 2007-03-20
ctrl+alt+F1
```
sudo dpkg-reconfigure xserver-xorg
```

---

