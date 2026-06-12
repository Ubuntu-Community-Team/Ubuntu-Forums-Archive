---
title: "No detecta la tarja de so"
date: 2010-02-15
forum: Catalan Team
---

### Post by lluisv on 2010-02-15
Salutacions!

Tinc instal·lat la darrera versió de l'UBUNTU en una màquina HP pavilion DV& i no em detecta la tarja de so.
Algú em pot ajudar a solucionar aquest problerma?

Gràcies!

---

### Post by lluisalguero on 2010-02-15
> **lluisv said:**
> Salutacions!

Tinc instal·lat la darrera versió de l'UBUNTU en una màquina HP pavilion DV& i no em detecta la tarja de so.
Algú em pot ajudar a solucionar aquest problerma?

Gràcies!

Sento no poder ajudar-te. Tinc la mateixa màquina que tu i em va funcionar tot a la primera.

Tranquil que entrarà algú i et donarà un cop de ma. Anims !!

---

### Post by kimet on 2010-02-15
En hauries de dir quina targeta de so porta.

```
lspci | grep Audio
```

Si es una intel HDA, pot ser que et serveixin aquestes adreces:
[http://edwardh.se/2010/02/06/compaq-610/](http://edwardh.se/2010/02/06/compaq-610/)
[http://www.esdebian.org/wiki/sin-sonido-tarjetas-hdaintel](http://www.esdebian.org/wiki/sin-sonido-tarjetas-hdaintel)
Vaig instal·lar kubuntu en un portàtil compaq i em vaig trobar amb el mateix problema que tu, amb la primera de les adreces ho vaig solucionar. 

Salut.

---

### Post by lluisv on 2010-02-15
Com puc saber quina tarja de so té el meu portàtil HP pavilion DV6?

---

### Post by PatrickVogeli on 2010-02-16
> **lluisv said:**
> Com puc saber quina tarja de so té el meu portàtil HP pavilion DV6?
cat /proc/asound/card*/codec#*  | grep Codec

---

### Post by Diegstroyer on 2010-02-19
Es estrany per que amb la versió 9.10 aquest model està completament suportat per el que es refereix al so.

Suposo que deus tenir la 9.04 instal·lada, de totes maneres et deixo un link a veure si t'ajuda.

Prova això: [http://gambasconchocolate.blogspot.com/2009/08/sonido-en-hp-pavilion-notebook-dv6.html]("http://gambasconchocolate.blogspot.com/2009/08/sonido-en-hp-pavilion-notebook-dv6.html")

---

### Post by argos3016 on 2010-02-19
aplay -l

---

### Post by papapep on 2010-02-20
lluisv: si et surt alguna cosa a l'ordre que t'ha dit, sense gaires explicacions :), en argos3016, enganxa-ho aquí. Si no et surt res, fes:

```
lspci | grep audio
```

i enganxa el que et mostri el terminal aquí.

---

