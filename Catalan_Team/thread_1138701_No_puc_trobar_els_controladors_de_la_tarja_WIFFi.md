---
title: "No puc trobar els controladors de la tarja WIFFi"
date: 2009-04-26
forum: Catalan Team
---

### Post by verif31 on 2009-04-26
Bon dia a tots,

Ja se que soc nou en aixó però desprès de deixar el Windows oer el Ubuntu m'ha deseparegut el Wiffi. Es un Wireless LAN Multiport W200 instalat d'origen en el Evo N610c (COMPAQ) .

Suposso que existeixen els controladors adecuats però per ara el sistema ni tant sols sap que està com a hardware. ¿No hi ha cap programa per baixar que m'actualitzi els controladors plug and play?

gracies.

---

### Post by papapep on 2009-04-26
Fes a un terminal:

```
lspci
```

i també:

```
ifconfig
```

i enganxa aquí el resultat d'ambdues ordres.

---

### Post by torracastanyes on 2009-04-26
Bona nit.

Jo també tinc el N610c, tot i que sence wifi.

Pel que sé, aquest W200, en realitat és un adaptador USB 1.1 amb xip AGERE y funciona amb els drivers Orinoco USB, segons diu aquí:

[http://www.svenkrahn.de/linux/CompaqEvoN610c/index.html](http://www.svenkrahn.de/linux/CompaqEvoN610c/index.html)

---

