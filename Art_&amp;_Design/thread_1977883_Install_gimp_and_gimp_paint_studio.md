---
title: "Install gimp and gimp paint studio"
date: 2012-05-10
forum: Art &amp; Design
---

### Post by DMKryl on 2012-05-10
hello I've trying to install gps without breaking gimp 2.8, there is any way to install both programs, without over writing each other?

---

### Post by hansdown on 2012-05-10
Hi, DMKryl.

Starting with Gimp installed, add the PPA.

```
sudo add-apt-repository ppa:shnatsel/gimp-paint-studio
```

```
sudo apt-get update
```

```
sudo apt-get install gimp-paint-studio
```

Check the link below.

[http://www.webupd8.org/2011/02/gimp-painter-and-gimp-paint-studio.html](http://www.webupd8.org/2011/02/gimp-painter-and-gimp-paint-studio.html)

---

### Post by DMKryl on 2012-05-11
The problem is that it overrides gimp, and i want to have both, gimp alone without gimmicks, and the gimp paint studio aside

---

