---
title: "ctrl V"
date: 2023-08-25
forum: Catalan Team
---

### Post by josep-maria on 2023-08-25
Quan sóc al whatsapp, no funciona el ctrlV. Fa unes setmanes anava bé. Ha deixat de funcionar de cop, sense que jo hagi fet res. Sí que funciona fora del whatsapp. Els ho he dit a l'ajuda del whatsapp, però diuen que ells ho tenne tot bé.
No he trobat res de semblant al fòrum. Tinc l'ubuntu 22.04.3 mate 1.26.0

---

### Post by ffp on 2023-08-27
A mi també em passava i no tinc ni idea del perquè, però avui ho he provat i funciona perfectament. Tinc Ubuntu 23.04 Gnome

---

### Post by wgarcia on 2023-08-28
Whatsapp? Suposo que us referiu a l'accés a Whatsapp mijtançant el navegador web, perquè no hi ha cap client de Whatsapp per a Linux. En aquest cas, si ctrl-v deixa de funcionar no hauria de funcionar en tot el navegador, i potser en cap lloc del sistema, no sols a la webapp del Whatsapp. 

És possible que alguna aplicació que teniu estigui afectant aquest funcionament. Es pot provar donar la següent ordre des d'una terminal:

```
ibus restart
```

Això reiniciarà la interfície que controla el funcionament del teclat. Però també convé pensar si alguna altra aplicació està interferint perquè deixi de funcionar.

---

### Post by josep-maria on 2023-08-29
Primer m'ha dit:
user@user-OptiPlex-3020:~$ ibus restart
No s'ha trobat l'ordre 'ibus', però pot ser instal·lada amb:
sudo apt install ibus
Li dic:
user@user-OptiPlex-3020:~$ sudo apt install ibus

I després em diu:
user@user-OptiPlex-3020:~$ ibus restart
No es pot connectar amb l'IBus.

---

### Post by wgarcia on 2023-09-04
No entenc perquè ho marques amb "Solved" si la solució no ha funcionat.

Aquí n'hi ha una altra:

Ves a la pàgina "about:config" entrant això a la barra de navegació.

Busca la propietat "dom.event.clipboardevents.enabled" i marca-la com a "true".

---

