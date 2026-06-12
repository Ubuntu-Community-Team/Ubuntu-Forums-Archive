---
title: "Com puc eliminar una Partició sense fer-me mal"
date: 2007-05-31
forum: Catalan Team
---

### Post by manelolesa on 2007-05-31
Despres de fer el tema amb un LIVE CD.

ERROR Grub 22, no he tingut nassos de tornar a la vida l'arranc del PC.

Per tant INSTALL i andando.

Salut

[I]
Tinc un Disc Dur amb  Ubuntu, Debian i Windows. El Boot esta en la Partició de Windows.

Vull eliminar la partició de Debian per quedar-me amb les altres dues i desprès redimensionar la d'Ubuntu.

Fa poc vaig fer la mateixa operació, tenia Ubuntu, Suse i Windows, vaig eliminar el Suse i el Grub donava errors i no podia arrencar el PC. Vaig tenir que tornar a instal•lar l'Ubuntu per arreglar el tema ja que despres de provar les solucions que vaig trobar als Forums no va haver manera de arreglar-ho.

Ara vull anar sobre segur, per això us demano consell, abans de tornar a “cagarla”.

Gracies

Manel[/I]

---

### Post by patrickfromspain on 2007-05-31
mmm no es dificil. Assegura't que el grub que tens es el d'ubuntu; si no es aixi, fes en un terminal sudo grub-install hd0. Despres, fent servir un livecd, elimina la particio de debian i fes més gran la d'ubuntu. Pot ser que no t'arranqui perque el disc d'ubuntu ha canviat de nom. Llavors en el grub edita la linea pertinent i on hi posi root=/dev/sda6 proba sda5 o alguna cosa aixi.

salut!

---

### Post by lluis.dalmau on 2007-05-31
Una bona eina per fer-ho és el gparted que trobaràs a qualsevol live-cd que t'ajudarà a fer això que necessites.

Això sí, abans de fer una operació d'aquestes característiques és recomanable que tinguis còpia de seguretat o alguna imatge ;)

---

### Post by orestesmas on 2007-06-01
Ja t'ha apuntat algunes solucions, bàsicament has de vigilar de no eliminar la partició un tinguisel GRUB (o part d'ell) instal·lat.

D'altra banda, el GRUB és un gestor d'arrencada molt potent, perquè no necessita cap kernel per poder llegir diferents sistemes de fitxers i anar a buscar els diferents kernels (windows, linux...) a les seves ubicacions del disc. Per tant, és molt interessant tenir el GRUB instal·lat en un disquet i conèixer les seves [ordres bàsiques.]("http://www.gnu.org/software/grub/manual/grub.html"). Jo t'ho recomano vivament si fas experiments amb les particions. Sempre podràs arrencar un sistema del qual t'hagis carregat el gestor d'arrencada però que encara conservi els kernels al disc.

---

### Post by manelolesa on 2007-06-04
Despres de fer el tema amb un LIVE CD.

ERROR Grub 22, no he tingut nassos de tornar a la vida l'arranc del PC.

Per tant INSTALL i andando.

Salut

---

### Post by papapep on 2007-06-04
Però aleshores no pots posar resolt a l'assumpte, perquè no has resolt el problema. El proper cop que et torni a passar tornaràs a estar al mateix punt.

---

