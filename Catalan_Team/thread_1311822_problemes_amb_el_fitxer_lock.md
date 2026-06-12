---
title: "problemes amb el fitxer lock"
date: 2009-11-02
forum: Catalan Team
---

### Post by castanyeta on 2009-11-02
Companyes i companys,

Sóc nova en aquest fòrum i no massa experta, però confio en vosaltres perquè força vegades hi he trobat solucions.

Fa dos dies vaig actualitzar el meu Ubuntu al nou Karmic Koala (9.10). Ara volia convertir un rpm (AdobeReader_esp-8.1.7-1.i486) a deb per poder-lo instal·lar directament amb l'instal·lador de paquets Debian.

A la consola escric: susanna@castanyeta:~$ sudo apt-get install alien
i em torna:
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: No s'ha pogut blocar el directori d'administració (/var/lib/dpkg/). Hi ha algun altre procés que l'estigui utilitzant?

Vaig a comprovar el directori corresponent i veig això (imatge adjunta).

Em podeu donar un cop de mà per arreglar el problema? Moltes gràcies per endavant.

---

### Post by papapep on 2009-11-02
Hola, Castanyeta, benvinguda.

Això sol passar quan es tenen dues aplicacions de gestió de paquets intentant accedir simultàniament a la base de paquets.
Has provat a reiniciar per eliminar el bloqueig i assegurar-te que cap aplicació ha quedat penjada bloquejant l'altra?

---

### Post by castanyeta on 2009-11-06
Moltes gràcies! Ja està solucionat. Ja vaig fer bé, de confiar en vosaltres ;).

---

