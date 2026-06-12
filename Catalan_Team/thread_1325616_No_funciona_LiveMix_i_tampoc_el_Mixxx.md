---
title: "No funciona LiveMix i tampoc el Mixxx"
date: 2009-11-13
forum: Catalan Team
---

### Post by lFossil on 2009-11-13
Hola!
Ja fa temps que el Mixxx a voltes no em funcionaven les cançons i ara he provat de baixar-me aquest programa el LiveMix i em surt [això]("http://img697.imageshack.us/i/capturaq.png/")

No entenc què hi passa, algú li ha passat?
Gràcies

---

### Post by papapep on 2009-11-13
No tinc idea del tema del Livemix ni del Mixxx, però el missatge et diu explícitament que no tens el dimoni **[jackd]("http://linux.die.net/man/1/jackd")** executant-se.

Prova a instal·lar-lo:

```
sudo aptitude install jackd
```

un cop instal·lat, verifica que el tens funcionant:

```
ps -e|grep jackd
```

un cop vegis que està funcionant, torna a provar el que sigui que fessis que et provocava l'error que has mostrat.

---

### Post by sordoman on 2009-11-14
Hola IFossil,

Totalment d'acord amb en papapep, l'únic que has de tenir en compte es que, per defecte, quant instales jack esta posada l'opció "realtime", si no tens un nucli que ho soporti, no podras arrancar-lo, has d'hanar a "setup" i "desclickar" l'opció realtime.

sort):P

---

