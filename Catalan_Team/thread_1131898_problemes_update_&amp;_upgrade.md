---
title: "problemes update &amp; upgrade"
date: 2009-04-21
forum: Catalan Team
---

### Post by jrosell on 2009-04-21
Sóc l'unic que té problemes per actualitzar ubuntu intrepid ?!
Errors de checksum, etc...
Em podeu donar un sources.list que funcioni!?
Jo utilitzaba fonts internacionals i vaig provar de utilitzar les de "us"...

---

### Post by lluisanunez on 2009-04-21
Jo fa temps que no tinc cap problema. De vegades no faig ni checksum. Vaig triar Rediris el dia que m'el vaig instal·lar.
Aquí tens un resum del meu  sources.lst:
```
deb http://es.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://es.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://es.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://es.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid-updates universe


deb http://es.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://es.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse


```

---

