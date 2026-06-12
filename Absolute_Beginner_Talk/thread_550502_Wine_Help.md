---
title: "Wine Help"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-13
opened synaptic package manager
tryed to install wine:
this is error i get
wine:
  Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libgphoto2-2 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.0.3-1ubuntu5 is to be installed
  Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
  Depends: libxslt1.1 (>=1.1.20) but 1.1.15-1ubuntu1 is to be installed

---

### Post by huangweiqiu on 2007-09-13
If you install the Wine from source,I don't think will cause this problem.

Which source are you using??

---

### Post by Tootles on 2007-09-13
how do u install it from source

---

### Post by splintercellguy on 2007-09-14
What version of Ubuntu are you using? Are you using Gutsy? Have you tried following the directions from: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) ?

---

### Post by Maestro23 on 2007-09-14
> **splintercellguy said:**
> What version of Ubuntu are you using? Are you using Gutsy? Have you tried following the directions from: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) ?

Beat me to it. :smile:

---

### Post by Tootles on 2007-09-14
how do i run an exe file with it

---

### Post by Amazona aestiva on 2007-09-14
Type:
```
wine ....exe
```
Example:
```
wine '/home/nandor/.wine/drive_c/Program Files/The Adventure Company/Aura 2 The Sacred Rings/TSR.exe'
```

---

### Post by Tootles on 2007-09-14
how do u tell if u have wine installed

---

### Post by Maestro23 on 2007-09-14
> **Tootles said:**
> how do u tell if u have wine installed

Open terminal:

> whereis wine

Should see[COLOR="Red"] /usr/bin/wine[/COLOR]

---

