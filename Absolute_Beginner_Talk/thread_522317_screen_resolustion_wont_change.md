---
title: "screen resolustion wont change"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jasond123 on 2007-08-10
hi, need some help. my screen resolution was working fine at 1024*760 but today when i started up my pc it was set back too 800*600 and when i try and change it back it only gives me the option for 800*600. i think this problem started after a update but cant be sure. it will explain it happening out of the blue. Please Help.
Thanks

---

### Post by Ek0nomik on 2007-08-10
> **jasond123 said:**
> hi, need some help. my screen resolution was working fine at 1024*760 but today when i started up my pc it was set back too 800*600 and when i try and change it back it only gives me the option for 800*600. i think this problem started after a update but cant be sure. it will explain it happening out of the blue. Please Help.
Thanks

Accessories/Terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use tab to move around, spacebar to select.

Select your video card drivers, and then you can select the desired resolutions.

---

### Post by Quinn5219 on 2007-08-11
> **Ek0nomik said:**
> Accessories/Terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use tab to move around, spacebar to select.

Select your video card drivers, and then you can select the desired resolutions.

Good Luck.  Been trying to solve a similar problem for 6 months.  Not sure, but I think the Ubuntu
fairy shows up around November.

---

