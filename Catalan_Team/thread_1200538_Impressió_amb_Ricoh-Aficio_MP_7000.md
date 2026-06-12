---
title: "Impressió amb Ricoh-Aficio MP 7000"
date: 2009-06-30
forum: Catalan Team
---

### Post by SiscoGarcia on 2009-06-30
A l'[institut]("http://centre.iestorrevicens.cat/") on treballo tenim una impressora [Ricoh Aficio-MP7000]("http://www.ricoh.es/products/copiers/largeworkgroup/mp7000.xhtml") que vam aconseguir que funcionés bé amb la intrepid, però des que hem actualitzat a jaunty ens trobem amb un seguit de caràcters erronis impresos aleatòriament. El problema és que ho hem observat després d'haver instal·lat la **jaunty a les 5 aules d'informàtica** :p que tenim (un centenar de màquines aproximadament). El [driver]("http://www.openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_MP_7000") és el que proporciona Ricoh però modificat perquè reconegui usuaris (hi havia un problema amb el codi d'usuari).

Sospitem que amb el canvi de versió d'ubuntu hi ha hagut alguna mena de problema amb el reconeixement del driver però se'ns escapa. Ens podeu donar un cop de mà?

Agraïts.

---

### Post by papapep on 2009-06-30
[http://tinyurl.com/mdqvms](http://tinyurl.com/mdqvms)

[http://ubuntuforums.org/showthread.php?t=1117723](http://ubuntuforums.org/showthread.php?t=1117723)

En síntesi, que si feu servir el controlador CUPS+Gutenprint v5.2.3 Simplified diu que torna a funcionar correctament i ja no surten els caràcters estranys.

---

### Post by SiscoGarcia on 2009-06-30
> **papapep said:**
> [http://tinyurl.com/mdqvms](http://tinyurl.com/mdqvms)

"Ahí m'has dao"; no havíem fet aquesta cerca, sí d'altres però no ens havien retornat aquest resultat. Per cert, com ho has fet? Amb el [recordmydesktop]("http://linux.softpedia.com/get/Multimedia/Graphics/gtk-recordMyDesktop-21337.shtml")?

> **papapep said:**
> [http://tinyurl.com/mdqvms](http://tinyurl.com/mdqvms)

[http://ubuntuforums.org/showthread.php?t=1117723](http://ubuntuforums.org/showthread.php?t=1117723)

En síntesi, que si feu servir el controlador CUPS+Gutenprint v5.2.3 Simplified diu que torna a funcionar correctament i ja no surten els caràcters estranys.

Merci papapep, és el mateix problema que tenim a l'insti. Dijous o divendres mirarem de resoldre-ho i ja us explicarem.

---

### Post by SiscoGarcia on 2009-08-31
Recupero aquest fil per comunicar que el problema s'ha resolt en fer-se l'última actualització. Vam provar la solució que suggeria el papapep (gràcies) i d'altres possibilitats seguint el fil que ens recomanava; però no ha estat fins avui que, en tornar de les vacances i actualitzar màquines hem comprovat que la impressió ja és correcta.

Aprofito per dir que amb Karmic la impressora funciona correctament.

---

