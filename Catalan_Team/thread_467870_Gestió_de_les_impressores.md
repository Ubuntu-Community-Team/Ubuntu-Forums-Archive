---
title: "Gestió de les impressores"
date: 2007-06-08
forum: Catalan Team
---

### Post by lluis.dalmau on 2007-06-08
Segur que hi deu haver algun programa que pot servir per gestionar les impressores i les diferents ordres d'impressió que fan els usuaris.

M'agradaria conèixer la vostra experiència perquè al nostre institut ens estem plantejant com podríem posar en funcionament un sistema en el qual els usuaris puguin enviar les impressions a les impressores però aquestes es gestionin adequadament

Això ho podem aconseguir fent que qui necessiti una impressió s'identifiqui, enviant les impressions automàticament a impressores d'alt volum (impressió més econòmica) i evitant que des de les aules s'enviïn impressions indiscriminadament a qualsevol impressora.

Gràcies !

---

### Post by elbuit on 2007-06-09
Hola Lluís.
Supose que el que vols és que cada alumne/professor tinga un nom d'usuari i una paraula de pas per a identificar els treballs i posar quotes per usuari, ... 
La cosa no és trivial (si el que vols es fer el que he posat abans) i pots trobar un document que ho explica ací emprant pykota:
[http://es.tldp.org/Tutoriales/doc-openldap-samba-cups-python/htmls/](http://es.tldp.org/Tutoriales/doc-openldap-samba-cups-python/htmls/)

Per altra banda, si el que vols és simplement fer que un PC faça de servidor d'impressió amb el cups (amb samba) que ve per defecte en Ubuntu ja ho pots fer.


També hi han impressores (models més avançats) que amb el driver (de windows) demanen una contrassenya (per a restringir qui imprimeix) de forma que després es va a la reprografia i li dius que t'imprimeisca eixe treball. El de reprografia al final del dia borra tots els treballs en cua de la impressora que no ha anat ningú a reclamar-los (obviament la impressora pausa tots els treballs que li entren)

Espere que t'haja servit d'ajuda.
Un abraç

---

