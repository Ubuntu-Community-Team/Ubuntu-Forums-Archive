---
title: "Question about upgrading"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-01-04
Tomorrow i will be fitting a new graphics card and i'm just wondering how to go about it in Ubuntu. Currently i have an ATi X800XT and i'll be fitting an Nvidia 7800 GTX. I installed the binary drivers from ATi's website and modified my xorg.conf to use them. Should i remove the drivers before fitting my new card or does it not matter? How do i remove them, not too sure where they're installed etc...

Thanks in advance :)

---

### Post by taurus on 2007-01-04
Put the new card in.  Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

