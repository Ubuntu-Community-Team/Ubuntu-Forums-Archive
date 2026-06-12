---
title: "moving desktop icons to other file locations"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by CAMEMBEAR on 2008-03-24
I downloaded a font file from the internet & it is on my desktop as an icon - how can I remove it from the desktop without removing it from the computer to use with other applications etc?

---

### Post by jan quark on 2008-03-24
try this small guide for adding fonts in ubuntu
[http://ubuntuhelp.piranho.de/gimp8.html](http://ubuntuhelp.piranho.de/gimp8.html)

after this you can delete it from the desktop

---

### Post by jslman on 2008-03-24
In your home directory you will find a directory named with your login name an in that a directory with the name "Desktop". In this directory you will probably find the downloaded file. 

To do so via cli:

```

sudo cp /home/username/Desktop/urfile.ext /home/username/.fonts

```

or 

```

sudo cp /home/username/Desktop/urfile.ext /usr/share/fonts

```

Jeroen

---

