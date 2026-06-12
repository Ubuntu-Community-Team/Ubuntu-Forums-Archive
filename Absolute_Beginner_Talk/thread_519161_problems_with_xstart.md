---
title: "problems with xstart"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by MrPhen on 2007-08-06
when i do xstart i get the following errors:

(EE) VESA(0): No matching modes
(EE) Screen(s) found but none have a usable configuration.

...help? :confused:

---

### Post by arijarot on 2007-08-06
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by milosz.galazka on 2007-08-06
Hello,

You should provide some information about graphic card that you are using so maybe someone  will know solution.

You could try reconfiguring X by executing command
*sudo dpkg-reconfigure xserver-xorg*

---

### Post by MrPhen on 2007-08-07
i've tried both multiple times, never seems to work after i'm done.

---

### Post by arijarot on 2007-08-07
what kind of graphics card are you using/ is  it enabled?

---

### Post by MrPhen on 2007-08-07
> **arijarot said:**
> what kind of graphics card are you using/ is  it enabled?

CARD (CIRCUIT), GRAPHICS, 128MB, M52, I6400 (ATI X1300)
I'm pretty sure it is although not 100%, anyway to tell?

---

