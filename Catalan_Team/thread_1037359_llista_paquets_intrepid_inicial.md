---
title: "llista paquets intrepid inicial"
date: 2009-01-11
forum: Catalan Team
---

### Post by trinkus on 2009-01-11
Tinc una pregunta una mica rara...
Hi ha alguna manera d'obtenir alguna llista dels paquets que la ubuntu instala per defecte, vull dir que quan instales la intrepid de primeres... quins paquets hi posa? Com puc saber si n'he esborrat algun i tornar-lo a posar, per exemple?

Gracies

---

### Post by orestesmas on 2009-01-11
Agafa un sistema net (pot ser un CD autònom), obre un terminal i posa

```

dpkg --get-selections > paquets_per_defecte.txt

```

Llavors et crearà un fitxer amb les seleccions de paquets del sistema actual.

Si mai vols saber si has fet variacions en els paquets només cal que repeteixis l'ordre, gravant la sortida a un altre fitxer, i comparant el fitxer original amb l'actual.

---

### Post by trinkus on 2009-01-12
Concret i practic. Merci

---

