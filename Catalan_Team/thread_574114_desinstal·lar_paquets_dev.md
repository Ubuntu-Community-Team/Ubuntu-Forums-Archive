---
title: "desinstal·lar paquets dev"
date: 2007-10-12
forum: Catalan Team
---

### Post by muleta on 2007-10-12
Com es desinstal·len els programes dev?.

---

### Post by papapep on 2007-10-12
A què et refereixes amb "paquets dev"?

---

### Post by muleta on 2007-10-12
PERDONA, [-o<[-o<[-o<. Volia dir ```
deb
```

---

### Post by pespin on 2007-10-12
Et refereixes a paquets instal·lats per separat (per exemple amb dpkg) o instal·lats dels repositoris (via Synaptic, Adept, aptitude, apt-get) ?

---

### Post by muleta on 2007-10-12
Em refereixo a programes.deb que s'autoinstal·len amb dpkg quan els descarego.

En concret, vaig instal·lar així l'AVG antivirus pro i no em funciona perque demana un registre que ja tinc fet però no sé com indicar-li.

Observo que és per a Servidors i voldria instal·lar el gratuït per a usuari simple però no el puc instal·lar. Potser és perque hauria de desinstal·lar la versió instal·lada.

Faix ```
sudo aptitude purge AVG
``` i no em canvia res. Diu allò de que no es canviaran, instal·laran ni desinstal·laran paquets.

---

### Post by RainCT on 2007-10-12
Dubto que el nom del paquet sigui "AVG". Busca'l al Synaptic millor (si has insta&#320;lat algun paquet extern hi surt, encara que no estigui als repositoris).

---

### Post by muleta on 2007-10-12
Gràcies, l'he pogut desinstal·lar completament amb el Synaptic, però no ha servit de res perque continuo sense poder instal·lar-lo. M'indica que s'està fent i que s'ha fet amb èxit però no el trobo enlloc, ni tan sols amb el cercador de fitxers.

L'he descarregat de:

[http://www.grisoft.com/doc/31/la-es/crp/0?prd=avl](http://www.grisoft.com/doc/31/la-es/crp/0?prd=avl)

He triat la opció deb. M'he equivocat?.

---

### Post by papapep on 2007-10-12
Personalment, l'únic error que crec que comets és instal·lar-te un antivirus a un ordinador amb linux. No et cal per a res. 

L'estructura de permisos i seguretat que porten els sistemes derivats de Unix (Linux, BSD, etc) eviten aquesta problemàtica.

Això no vol dir que no puguis fer-ho, però es com anar a vendre neveres al Pol Nord. :-)

---

### Post by muleta on 2007-10-13
Ja sé que ho dieu i és molt tranquil·litzador però estic tan escarmentada amb Windows que no puc deixar de buscar seguretat. 

D'altra banda, llegeixo coses com aquesta: ```
Según reporta el US-CERT (United States Computer Emergency Readiness Team) en su informe de final de año, Windows tuvo menos vulnerabilidades que Linux y Unix durante todo el 2005.
De enero a diciembre, la cantidad de vulnerabilidades detectadas en Windows, ascendió a 812, contra 2328 descubiertas en el mismo periodo en sistemas Linux y Unix.

Y si lo dice el CERT creo que va en serio, ademas lo considero neutral.
```

i em tornen els dubtes. A més, com que descarrego molts fitxers amb l'amule, em costa d'entendre que ja no m'afectaran tots els atacs que entraven al meu pc a través del 80 % de fitxers que descarregava amb l'emule o que m'arribaven amb el correu electrònic, en forma d'autoexecutables, tot i els filtres.

Allà, a més de dos potentíssims firewalls, havia de tenir diversos antiivirus instal·lats que s'autoactualitzaven a diari, antispywares, netejadors de disc, reparadors de pc i efectuar moltes netejes periódicament. Trobava el sistema ple d'errors cada vegada i era una feinada.

Com que aquí també descarrego i autoexecuto, és normal que desconfïi.

---

### Post by anigwei on 2007-10-13
Tal com diu el papapep no et cal per a res, dona-li un vot de confiança :)

Estem malacostumats al windows, que a sobre de car, és un colador. I per tapar els forats hem d'utilitzar eines externes que relantitzen el funcionament.

Amb Linux una possible justificació de l'antivirus és per al correu, i no per a nosaltres, sinó per als possibles receptors, d'estar segurs que no rebem o reenviem un correu amb virus. A nosaltres no ens afectaria però al destinatari "windowser" sí.

I respecte el firewall tampoc cal patir.

Salut!

---

### Post by Ferri on 2007-10-13
```
sudo dpkg -r nom_del_paquet
```
D'acord amb el que s'ha dit de la necessitat (o no) d'antivirus a linux.
No estic tant segur de que no hi hagi necessitat de tallafocs, però. Si et connectes fent servir un router, probablement no calgui, però si tens una connexió directa penso que està de més.
De fet, és bastant més fàcil trobar tallafocs per a linux que no antivirus (algunes distribucions el porten per defecte). Suposo que per alguna cosa deu ser...

---

### Post by papapep on 2007-10-13
La necessitat d'un tallafocs Ferri, és directament proporcional als serveis que tinguis funcionant i que tinguis oberts al món. Si no en tens, no ofereixes res ;-)

Tot i això, cert és que tenir un tallafocs no és cap disbarat. I, per cert, tots els "tallafocs" que jo conec per a linux, són símplement una interfície gràfica per a l'[iptables]("http://es.wikipedia.org/wiki/Iptables").

---

