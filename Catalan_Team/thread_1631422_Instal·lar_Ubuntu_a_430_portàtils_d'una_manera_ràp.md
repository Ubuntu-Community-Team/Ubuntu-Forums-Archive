---
title: "Instal·lar Ubuntu a 430 portàtils d'una manera ràpida?"
date: 2010-11-26
forum: Catalan Team
---

### Post by mrc2407 on 2010-11-26
Bones!

M'han encarregat el manteniment de 430 (si no m'equivoco) netbooks d'un institut que participa al famós projecte 1x de la Generalitat. El cas és que no suporto Linkat (ni l'aspecte, ni que estigui basat en openSUSE, ni que els responsables es neguin a actualitzar a OpenOffice 3.2 si la 3.1.1 ja funciona... l'únic que hi ha de bo és la quantitat de programes que hi ha) i amb el coordinador d'informàtica del centre parlàvem de passar-los a Ubuntu.

Això genera alguns problemes:

1) Com podem instal·lar i configurar Ubuntu d'una manera ràpida en tal quantitat d'ordinadors? No n'hi ha prou amb fer un sol usuari admin, sinó que a més caldria crear un usuari "alumne" i tallar-li permisos perquè no pugui ni actualitzar ni instal·lar res... No és plan que es passin les classes jugant!

2) Com podem restaurar ràpidament TOT el disc d'un ordinador? Els portàtils vénen per defecte amb Win7 i Linkat, i ens interessaria que, si mai passa alguna cosa, poguéssim reinstal·lar ràpidament els dos sistemes operatius i les particions que hi hagi al disc dur... Alguna idea?

Se m'haia acudit que, per instal·lar ràpidament, potser n'hi ha prou amb configurar un sol ordinador i després clonar-lo d'alguna manera als altres, però no sé si és factible fer-ho, ni si hi hauria problemes amb les adreces MAC de cada portàtil o coses semblants... algú té alguna idea sobre el tema? :)

Sincerament, no entenc perquè la Generalitat es dedica a crear una nova distro tenint-ne de bones com Ubuntu corrent perfectament... Només calia que fessin un repositori de programes, o que pengessin scripts de configuració ràpida! Quina manera de gastar els diners...

Gràcies a tots! :)

---

### Post by Albert Que on 2010-11-26
Estic amb tu respecte això del linkcat que dius, una mala eina que només afavoreix que qui la provi pensi que tot el linux és una me***. No he entès perquè cal que la Generalitat destini recursos a fer i a mantenir la seva pròpia distribució si n'hi ha de fetes que funcionen de perles.

Els que hauria de fer la Generalitat és traduir sistemàticament qualsevol aplicació de codi obert que corri pel món, amb una bona memòria de traducció això és bufar i fer ampolles i deixar-se de reinventar la roda.

Per fer el que dius jo agafaria un portàtil i el deixaria net i polit exactament com els voldries tots, i crearia una imatge del disc dur (amb una liveCD del clonezilla, per exemple).

Després desaria la imatge al servidor i per xarxa aniria instal·lant la imatge a cada un dels portàtils (amb el mateix clonezilla). Si no tots els 430 portàtils són iguals potser hauries de fer una imatge per cada model. Hi pots tenir tantes imatges com t'interessi: una pels portàtils dels professors, per diferents tipus d'alumnes...

El primer cop seria una matada, però els pots deixar endollats tota la nit i anar-ho fent per tongades. Si algun es desconfigura només et caldria reinstal·lar la imatge.

Segur que hi ha algú que en sap més i et dóna una solució millor. Sort!!

---

### Post by wgarcia on 2010-11-27
Estic d'acord amb l'Albert que hi ha procediments per distribuir Ubuntu (o qualsevol altra distribució) a llarg escala, potser algun/a altre/a amb més experiència d'això pugui donar algunes referències millors, però per començar no està malament:

[http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install)

Ara bé, voldria trencar una llança sobre el projecte Linkat, i aclarir algunes coses, però ho faré en un altre fil.

---

### Post by wgarcia on 2010-11-27
Obro un altre fil sobre Linkat vs. Ubuntu.

També dir que hi ha d'altres instituts que també han adoptat Ubuntu les experiències dels quals et poden ser d'utilitat.

---

### Post by kimet on 2010-11-27
Per clonar discs es pot fer servir la comanda dd. Ara be, les UUID serán diferents i s'haurà de configurar l'fstab i reinstal.lar GRUB al MBR.

Una altra forma es usar debootstrap per instal.lar el sistema i chroot per a configurar-lo, es pot fer un script que corri desde un llapis USB sense gaires complicacions.

Salut.

---

### Post by epages on 2010-11-27
(comentari mogut al fil [Linkat vs. Ubuntu]("http://ubuntuforums.org/showpost.php?p=10169482&postcount=4"))

---

### Post by SiscoGarcia on 2010-11-30
> **wgarcia said:**
> Obro un altre fil sobre Linkat vs. Ubuntu.

També dir que hi ha d'altres instituts que també han adoptat Ubuntu les experiències dels quals et poden ser d'utilitat.

Com [he apuntat]("http://ubuntuforums.org/showpost.php?p=10183559&postcount=11") en el [fil sobre Linkat vs. Ubuntu]("http://ubuntuforums.org/showthread.php?t=1631729"), l'experiència que tenim al respecte no és en els portàtils del projecte Educat1x1, sinó en la [migració de totes les màquines de sobretaula del centre a l'Ubuntu]("http://ponent.caliu.cat/2010/07/30/tot-linsti-amb-ubuntu/"). Com ja explico a l'altre fil, aquesta experiència [l'estem documentant]("http://iestorrevicens.xtec.cat/wiki/") (encara en una fase molt incipient) per si pot ser útil a més gent.

En qualsevol cas, si un centre complex com el nostre pot migrar a l'Ubuntu vol dir que el canvi és possible, només cal que hi hagi interès a fer-lo :D

---

### Post by mrc2407 on 2010-12-04
Ei, moltíssimes gràcies a tots, però al final sembla que al coordinador d'informàtica ja li està bé Linkat... :-|

De tota manera, m'apunto la idea del clonezilla per si de cas... :)

---

