---
title: "problemes amb ext4"
date: 2009-03-01
forum: Catalan Team
---

### Post by tanreb20 on 2009-03-01
Hola amics!

Avui he instalat la jaunty jackalope en mitg disc dur. Per estalviar-me problemas he decidit no instalar el grub.

El problema bé quan intento montar la partició del jauntu per poder veure els arcius vmlinuz i initrid que necessito per indicar al grub que s'ha de carregar.

No em deixa montar la meva particio jaunty perqué l'ubuntu 8.10 no reconeix ext4.

Hi ha alguna manera de poder-ho fer?

Sino obriré amb un liveCD i provaré de fer-ho tot desde alli, pero particularment no m'agraden els liveCD's

Gracies per adelantat

---

### Post by CarlesOriol on 2009-03-02
He llegit dues solucions a [http://www.jmvoces.co.cc/2009/02/05/usar-ext4-en-ubuntu-810-parte-i/](http://www.jmvoces.co.cc/2009/02/05/usar-ext4-en-ubuntu-810-parte-i/)

jo personalment no faria cap de les dues.

---

### Post by tanreb20 on 2009-03-02
Si ja vaig provar la segona i res de res.

---

### Post by jordilin on 2009-03-04
No he llegit aquestes solucions apuntades per l'usuari CarlesOriol, pero basicament tens que recompilar el kernel en 8.10 per suportar ext4. Si no ets un usuari avançat, jo no tocaria el teu sistema operatiu de treball i estable, osease, 8.10, per muntar una particio ext4. Jo m'hauria de remuntar als meus anys d'usuari de Debian quan era necessari algunes vegades compilar el Kernel. Simplement, no val la pena a menys que vulguis aprendre a fons com funciona tot plegat i no et faci res petar el teu sistema estable.

---

### Post by tanreb20 on 2009-03-04
No em fa re spetar el kernel ja que tinc un d'emergengia

Actualment funciono amb el 2.6.27-11-generic i tinc el 2.6.27-7-generic com a suport d'emergencia.

Se me so  menys els passos que shan de ralitzar pero no trobo cap guia fiable al 100(ja vaig recompilar un kernel per un problema d drivers de fet :D)

Pero no m'en recordo de com es feia, ja que no són els tipics passos de

```
make
make install
```

---

