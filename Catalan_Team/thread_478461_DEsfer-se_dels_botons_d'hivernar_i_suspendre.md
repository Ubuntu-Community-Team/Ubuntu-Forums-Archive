---
title: "DEsfer-se dels botons d'hivernar i suspendre"
date: 2007-06-19
forum: Catalan Team
---

### Post by crazyserver on 2007-06-19
Semblarà una tonteria, però es pot fer alguna cosa perque no surtin els botos de suspendre i hivernar al premer el botó de sortir de l'ubuntu?

De tant en tant vaig atabalat que li dono a algun sense voler.. i com k jo no uso aquestes opcions...

Gràcies!

---

### Post by lsrg on 2007-06-19
atura el daemon acpi
/etc/init.d/acpid stop

et desapareixen?

---

### Post by crazyserver on 2007-06-19
Mmmmm No! Però merci!
No desapareixen... i suposo que quan reinicio torno a activar el servei...
He notat però que en un altre usuari no tinc els botons!
Pero no veig quina pot ser la diferencia... Permisos potser?

---

### Post by patrickfromspain on 2007-06-19
gconf-editor

apps -> gnome-power-manager -> destaxa can_hibernate i can_suspend.

Salut!

---

### Post by crazyserver on 2007-06-19
Gràcies!!!
Ara si!
Motles gràcies!

---

