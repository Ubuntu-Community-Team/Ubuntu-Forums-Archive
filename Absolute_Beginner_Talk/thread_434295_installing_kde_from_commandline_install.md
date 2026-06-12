---
title: "installing kde from commandline install"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-05-05
Hii guys

any of you know a link where it is clearly detailed how to install to a command line install so that I can then install kde on top of it. I prefer avoid the bloat of kubuntu and use the stability of the ubuntu core.

Cheers

Cippa

---

### Post by Bachstelze on 2007-05-05
Which Ubuntu release ?

---

### Post by Fitzy_oz on 2007-05-05
> **Cippa Lippa said:**
> Hii guys

any of you know a link where it is clearly detailed how to install to a command line install so that I can then install kde on top of it. I prefer avoid the bloat of kubuntu and use the stability of the ubuntu core.

Cheers

Cippa

I think you can do that with the alternate install cd ISO.  I think it's just a matter of doing a sudo apt-get install kde.

---

### Post by Cippa Lippa on 2007-05-05
yeah but I know I would also have to install xorg and other things. Do you guys kknow a list of the things to install

---

### Post by Cippa Lippa on 2007-05-05
> **HymnToLife said:**
> Which Ubuntu release ?
Feisty if possible

---

### Post by Bachstelze on 2007-05-05
Then just do

```
sudo apt-get install xorg kde
```

(you can replace kde with kde-core for a minimal but faster KDE)

---

