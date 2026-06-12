---
title: "Arrencada (Grub) a l'Aspire One"
date: 2012-08-01
forum: Catalan Team
---

### Post by grundt on 2012-08-01
Hola, estic instalant la distribució 12.4 en un Acer aspire one, que ja duia el windous 7.

Vaig crear el pendrive amb un mac i el programa unebootin.

En la instalació no hi ha hagut problemes, he fet una partició, i he deixat els dos sistemes, però al acabar i reiniciar, he tret el pendrive i...:

Ara, al arrencar el Acer Aspire One, només em deixa entrar amb el windous7, no hi surt el Grub.

En canvi si arrenco amb el USB posat, si que em surt el Grub.

Mmmmm, sabeu que està passant?

---

### Post by wgarcia on 2012-08-01
Segurament s'ha instal·lat el grub al pendrive i no al disc principal. Si saps quin és el disc que mira primer el sistema, suposant que estigui associat amb el dispositiu /dev/sda, la instrucció per a instal·lar-lo en aquest disc seria (des d'una terminal):

```
sudo grub-install /dev/sda
```

---

### Post by grundt on 2012-08-01
Fet!

L'has clavat.

Merci

---

