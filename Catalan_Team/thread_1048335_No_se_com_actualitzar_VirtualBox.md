---
title: "No se com actualitzar VirtualBox"
date: 2009-01-23
forum: Catalan Team
---

### Post by MiquelBLL on 2009-01-23
Tinc instal.lat el VirtualBox 2.0.4 funcionan be, pero ja es la segona vegada que no puc actualitzar-lo, intento instal.lar la nova versio 2.1_2.1.2 i em diu que entra en conflicte amb la versio anterior. Es la versio per AMD i per Intrepid. Algu li passa? Gracies.

---

### Post by oriolsbd on 2009-01-23
> **MiquelBLL said:**
> Tinc instal.lat el VirtualBox 2.0.4 funcionan be, pero ja es la segona vegada que no puc actualitzar-lo, intento instal.lar la nova versio 2.1_2.1.2 i em diu que entra en conflicte amb la versio anterior. Es la versio per AMD i per Intrepid. Algu li passa? Gracies.
Si instal·les el VirtualBox amb un .deb, sempre has de desinstal·lar primer la versió anterior abans d'instal·lar la nova. Sobretot, desinstal·la-la sense fer "purge" per mantenir les màquines virtuals!

D'altra banda, el millor que pots fer és habilitar-te el dipòsit de VirtualBox, i així tindràs les actualitzacions automàtiques. Des de l'ordinador on estic no el tinc. Quan pugui te'l dic.

Salut!

---

### Post by oriolsbd on 2009-01-23
Per configurar el diposit del Virtualbox, has d'afegir aquesta línia al fitxer /etc/apt/sources.list:

```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

Precisament avui he tingut una actualització automàtica de Virtualbox (a través d'aquest dipòsit que t'indico). Fins ara hi havia la 2.1.0, i ara tinc la 2.1.2.

Salut!

---

### Post by CarlesOriol on 2009-01-24
> **oriolsbd said:**
> Si instal·les el VirtualBox amb un .deb, sempre has de desinstal·lar primer la versió anterior abans d'instal·lar la nova.

A mi no m'ha calgut fer-ho.

Pot ser que el Miquel estigui actualitzant de la versió lliure a la de sun?

---

### Post by trinkus on 2009-01-24
Jo el tinc instal·lat amb .deb i ahir en engegar-lo em va dir que hi havia una actualitzacio, la va baixar i jo la vaig instalar sense desinstalar l'amterior. Tot va correctament.

Aixo que dieu dels repositoris semblen els mateixos (no pas els ose lliures). Algu sap si son compatibles havent instal·lat els .deb, vull dir, cal desisntalar-los i fer anar paquets, que personalment trobo molt comode...

Gracies

---

### Post by MiquelBLL on 2009-01-26
Hola gracies per la informacio. Finses ara no em calia desinstal.lar cap versio anterior del VBox, i sempre les instal.lo  des de .deb. No faig servir la versio OSE, i finses fa 2 actualitzacions baixaba des de la pagina virtualbox.org la versio per AMD i per la versio d´ubuntu que tenia i em funcionaba. Mirare de posar lo del repositori a veurer que.

---

### Post by MiquelBLL on 2009-02-05
Hola. La manera amb que he instal.lat sense problemes la nova versió es des del Synaptic, el cual des-instal.la la versió anterior i instal.la la nova. He vist que a millorat el suport per dispositius USB. Salutacions.

---

