---
title: "Connexió wifi"
date: 2012-10-09
forum: Catalan Team
---

### Post by Canareu on 2012-10-09
Bon dia, 
Fa pocs dies vaig decidir instal·lar Xubuntu 12.04 a un laptop vell. Tot funciona de manera força correcta però la connexió a internet em genera algun problema, ja que normalment, quan engego l'ordenador no em funciona. L'única solució que he trobat fins al moment és habilitar i deshabilitar "la xarxa sense fils" i d'aquesta forma em connecta automàticament en la majoria de casos.

Salutacions!

---

### Post by wgarcia on 2012-10-09
Vols dir que li costa connectar-se a la xarxa wifi, o està cablejat?

---

### Post by Canareu on 2012-10-09
> **wgarcia said:**
> Vols dir que li costa connectar-se a la xarxa wifi, o està cablejat?

No està cablejat. Llavors quan inicio la sessió s'intenta connectar a la xarxa wifi, hi ha cops que ràpidament es connecta, però hi ha d'altres vegades que no s'arriba a connectar i demana reiteradament que introduïsca la contrasenya. És curiós perquè si no funcionés mai podria dir que és problema de la instal·lació de la targeta, dels drivers, però amb aquest comportament intermitent que té, vaig perdut.
D'altra banda també tinc un altre laptot, aquest corre amb windows, i no em dóna cap problema amb la connexió wifi.

---

### Post by akyra on 2012-10-11
Una cosa semblant m'havia pasat.

Has provat a parar, deixar 30s sense corrent, i engegar el router?

---

### Post by wgarcia on 2012-10-11
Saps quina és la teva targeta de xarxa inalàmbrica? 

Amb 

```
lspci
```

des d'una terminal, es podrà veure.

---

### Post by Canareu on 2012-10-11
> **wgarcia said:**
> Saps quina és la teva targeta de xarxa inalàmbrica? 

Amb 

```
lspci
```

des d'una terminal, es podrà veure.

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by wgarcia on 2012-10-12
Em sembla que aquesta no és la targeta inalalàmbrica, sinó la targeta "ethernet", és a dir per al cable de xarxa. No surt cap altra cosa que digui "wireless" o "broadcom" o quelcom així?

---

