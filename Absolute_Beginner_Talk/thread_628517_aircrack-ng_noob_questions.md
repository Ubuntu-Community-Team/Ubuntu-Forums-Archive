---
title: "aircrack-ng noob questions"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2007-12-01
I dont know which madwifi driver Im using so I dont know wich patch to get. Once I get the patch I need Ive no idea yet how to actually patch the driver. From there I think I can get things going. 

Anyone having a idea about what Im yabbering about feel free to shout some feedback! Thanks

---

### Post by jken146 on 2007-12-01
```
ifconfig
```

---

### Post by DestroyMicroshaft on 2007-12-04
bump?

---

### Post by seventhc on 2007-12-04
> **DestroyMicroshaft said:**
> bump?


I never knew exactly what this means, so I'm asking. What doest it mean when someone writes 'bump?' I've seen it many times.

---

### Post by cool_walking_ on 2007-12-04
> **seventhc said:**
> I never knew exactly what this means, so I'm asking. What doest it mean when someone writes 'bump?' I've seen it many times.

"Bumping" is the act of writing a reply to a thread, simply so that it gets pushed up to the top of the list of threads, so that hopefully more people will see it and reply.

To the OP: aircrack-ng has some good tutorials on [their site](http://www.aircrack-ng.org/doku.php).  Madwifi is one driver for a series of cards.  To find what card you have, type```
sudo lspci -v
```at a console. To find if the madwifi is loaded, type ```
lsmod
```

---

### Post by seventhc on 2007-12-04
> **cool_walking_ said:**
> "Bumping" is the act of writing a reply to a thread, simply so that it gets pushed up to the top of the list of threads, so that hopefully more people will see it and reply.

  That makes sense :) thanks for the info

---

