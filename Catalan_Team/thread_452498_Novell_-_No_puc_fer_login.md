---
title: "Novell - No puc fer login"
date: 2007-05-23
forum: Catalan Team
---

### Post by mlaboria on 2007-05-23
Hola a tothom!

Fa temps vaig instal·lar l'Ubuntu per fer alguna prova, ara que el vull tornar a recuperar, no recordo quin usuari vaig posar, ni quin password. Quan intento entrar com a root, em diu que el root no té permís per accedir...

Què puc fer???

Moltes gràcies!

---

### Post by orestesmas on 2007-05-23
Les ubuntu estan pensades per o utilitzar l'usuari root directament. No té contrasenya definida i no pots "entrar" com a root.

Ara mateix no puc provar-ho, però se m'acut que podries entrar en "mode manteniment" (una opció de l'arrancada) i llavors arribaràs a una consola d'administrador. Allí pots fer:

1) cat /etc/passwd
Això t'ensenya el fitxer amb els usuaris creats. Com que només n'hi haurà un, no et serà difícil reconèixer-lo. A més, deu ser l'últim de la llista.

2) Suposant, per exemple, que l'usuari sigui "pepet", llavors fes:
passwd pepet nou_password

Amb això canvies el password de l'usuari pepet.

Ara reinicia (apreta Ctrl+D) i ja podràs entrar amb el nou password definit.

Digues què tal ha anat

Salut.

---

