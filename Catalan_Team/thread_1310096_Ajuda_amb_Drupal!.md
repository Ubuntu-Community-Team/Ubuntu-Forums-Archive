---
title: "Ajuda amb Drupal!"
date: 2009-11-01
forum: Catalan Team
---

### Post by kukat on 2009-11-01
Algú em pot explicar per que tots els enllaços m'ixen així?
[http://pellikana.cat/](http://pellikana.cat/)

m'ha costat molt instal.lar el Drupal. No passava de la base de dades, i no em tirava cap missatge d'error!!!!
Al final he editat l'arxiu així a mà, i al final he pogut fer la instal.lació:

$db_url = 'mysql://nom_usuari:password@mysql4.000webhost.com/base_dades';
$db_prefix = '';

Però una vegada acabada aquesta.....Tots els enllaços estan mal! (els que apunten a l'interior de la web)

o siga: [http:///?q=admin](http:///?q=admin)
Deuria de ser: [http://pellikana.cat/?q=admin](http://pellikana.cat/?q=admin)!!!

El que fa també que no es vegen les imatges ni res de res! Algú sap que pot ser??? Porte tota la vesprada pegant-li voltes al tema del Drupal. 
Ah! Per cert, tinc també el subdomini: [http://magica-nit.pellikana.cat](http://magica-nit.pellikana.cat), amb Joomla....Pot ser tinga alguna cosa a veure???? 
Que coses mes estranyes! 
Salut!

---

### Post by kukat on 2009-11-01
Val, deu ser algun lloc que tendria que configurar el nom de la web??? 
per què m'he donat compte que falta lo de
pellikana.cat
Bé, miraré a veure!
Gràcies de totes formes!
Salut!

---

### Post by papapep on 2009-11-01
> m'ha costat molt instal.lar el Drupal. No passava de la base de dades, i no em tirava cap missatge d'error!!!!

Doncs això no és pas normal.

> Al final he editat l'arxiu així a mà, i al final he pogut fer la instal.lació:


No estaria malament que especifiquessis el fitxer. Jo ja sé que vols dir el settings.php, però podria no saber-ho :)

> $db_url = 'mysql://nom_usuariassword@mysql4.000webhost.com/base_dades';
$db_prefix = '';


> Però una vegada acabada aquesta.....Tots els enllaços estan mal! (els que apunten a l'interior de la web)

Jo et demanaria que expliquessis com instal·les el Drupal, sense pistes costa fer d'adiví.

---

### Post by kukat on 2009-11-01
#$base_url = 'http://pellikana.cat/';  // NO trailing slash!

He comentat aquesta línia, i ja funciona....No se...Tindre que aprendre mes anglès!

L'he instal.lat com diuen en diversos foros, i creant la base de dades abans en mysql. Però pot ser estiga relacionat amb el hosting gratuït 000webhost, per què començava la instal.lació i no podia passar de la pantalla de configurar les bases de dades...i no tirava cap missatge d'error...Però bé, ja esta tot arreglat...
Gràcies igualment!

Salut!

---

