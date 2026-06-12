---
title: "Ordinador bloquejat per uns segons"
date: 2009-11-17
forum: Catalan Team
---

### Post by jamasca on 2009-11-17
Hola bones,

Ja fa uns mesos que m'he registrat en aquest fòrum i volia fer la meva primera consulta.

Tenc instal·lat Ubuntu 8.04 - Hardy Heron. Tot funciona bé, però de tant el tant l'ordinador es queda bloquejat. M'explico. Per exemple, si estic mirant una pel·lícula la imatge es queda aturada, mentre que el so continua amb normalitat. Quan estic utilitzant el firefox, l'ordinador es queda bloquejat (no respon a res) durant uns segons i després funciona bé. Així amb altres aplicacions. He mirat de trobar la sol·lució però no acabo de trobar-la. He trobat consultes semblants en les que explica que el problema pot venir dels drivers instal·lats.

---

### Post by Diegstroyer on 2009-11-17
Dels drivers o de la memoria ram.

Pots mirar si hi han missatges als logs?

En una terminal:

dmesg | grep error

Estaria be que provessis un LiveCD a veure si et succeix el mateix.

Si es així, quin hardware tens?

---

### Post by jamasca on 2009-11-17
Al terminal surt això: 

[   29.067482] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

Demà provaré amb un Live CD a veure si també passa. 

Gràcies:D

---

