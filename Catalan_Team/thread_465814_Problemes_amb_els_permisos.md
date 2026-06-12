---
title: "Problemes amb els permisos"
date: 2007-06-06
forum: Catalan Team
---

### Post by josep314 on 2007-06-06
Voldria modificar una linea del text que tinc a /etc/apt/sources.list

Em diu que no tinc permís, i no em deixa guardar l'arxiu quan el modifico.

Com puc adquirir el perms necessari, o com esborrar i/o substituir el text., (vaig escriure "wget", en lloc de "get" i no em deixa tirar endavant.

---

### Post by papapep on 2007-06-06
L'únic que et cal és obrir un terminal i teclejar:

sudo gedit /etc/apt/sources.list

Et demanarà la teva contrassenya i podràs editar i desar el fitxer.

Salutacions.

---

### Post by Ferri on 2007-06-06
I si no t'agrada obrir la terminal, alt-F2 i posa-hi:
gksudo gedit /etc/apt/sources.list

---

