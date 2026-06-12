---
title: "Disc dur trencat?"
date: 2007-10-23
forum: Catalan Team
---

### Post by albello on 2007-10-23
Hola amics,

Des que vaig instal·lar la nova versió d'Ubuntu he anat patint una sèrie de desgràcies que m'han dut a poder utilitzar només el Live CD, perquè no hi forma de tocar el disc dur. Jo crec que se m'ha trencat el disc dur, però com que no tinc massa idea i a més ha coincidit amb l'actualització al Gutsy, m'agradaria conéixer la vostra opinió abans de canviar-lo. Ahí van els símptomes:

- Abans tenia dues particions, una amb Windows i l'altra amb Ubuntu (Feisty). La de Windows anava extremadament lenta, a pesar de no estar massa "brut", el sistema operatiu.

- Amb el temps, aquesta partició va deixar inclús d'arrencar.

- Una vegada instal·lada Gutsy (ja sense particions, utilitzant tot el disc dur) el sistema feia un xequeig cada cop que engegava l'ordinador, ja que trobava errors a "/dev/sda1". Una vegada feta, el sistema anava, encara que passaven coses extranyes, com la desaparició d'arxius sense motius aparents.

- Amb el temps, després del xequeig em deia que havia de reiniciar. A poc que ho penseu s'adonareu que aquest cercle acaba ràpidament amb la paciència de qualsevol, així que

- l'últim que he fet ha sigut provar d'instal·lar de nou tant la versió Gutsy com la Feisty, però al procés de particionat em diu que nones, que "la creació d'espai d'intercanvi a la partició no.5 de SCSI3 (0,0,0) (sda) ha fallat"...


Em toca canviar el disc dur no?

---

### Post by albert-I on 2007-10-23
Jo no soc partidari de compartir dos SO en un mateix disc, que es pot fer i fa molta gent, pero jo :( i si aixó i afegeixes el Windows doncs :(

Com tenies aquest disc dur? Sda1 era linux? com es que tens 5 particions?

Una de General, ara es diuen sda? que s'ha n'ha fet del hda1? dels hdb2?

---

### Post by papapep on 2007-10-23
Jo el que faria és intentar trobar alguna eina de diagnòstic de discs durs, alguns fabricants les ofereixen al seu lloc web, i verificar què li passa realment al disc dur abans de tirar-lo a la paperera.
Normalment es graven a un diskett o a un cd i s'executen en reiniciar el sistema.

---

### Post by albello on 2007-10-24
Hola Albert, jo tinc entés que sda1 és com anomena ubuntu al disc dur, independentment de les particions. Quan em va eixir aquell missatge d'error se suposa que tenia una única partició, no 5. Potser era la cinquena vegada que intentava instal·lar-lo, ves a saber.

Papapep, he mirat de fer el que m'has dit, però m'han sorgit un parell de problemetes tontos (un clàssic, vaja). Primer, l'arxiu que et dóna Seagate per fer el disquet d'arranc és massa gran (1.5 MB, per 1.44 MB de capacitat que tenen els disquets...), i quan he intentat utilitzar la versió de text, que si que cap, l'ordinador m'ha dit que el disc d'arranc té un error. A veure si esta vesprada puc gravar un CD i ja us dic com quede.

Adéu!

---

### Post by albello on 2007-10-24
Be, he pogut fer anar l'aplicacio de Seagate, que se suposa m'ha reparat els errors, i a mes, per si de cas, li he demanat que ho esborres tot. Despres he pogut instal.lar ubuntu, pero quan he reiniciat he tornat a tindre els mateixos problemes (quan esta carregant ubuntu es posa a fer un xequieg perque ha trobat problemes i em diu que reinicie).

Gracies pel vostre interes.

---

### Post by albert-I on 2007-10-25
No si ja ho he vist, pero es que les ultimes vegades que feia servir els noms de disc es deien hda1, hdb1 i així succesivament.

---

### Post by papapep on 2007-10-25
Albello: Doncs considerant que la eina de Seagate, com tu dius, ha intentat reparar els possibles errors, si un cop instal·lat l'Ubuntu torna a petar té molta pinta que realment el disc sigui defectuós. 
Tot i això, abans de tirar la tovallola, seria possible que ens enganxessis el missatge d'error que et dona el sistema en arrencar?

---

### Post by albello on 2007-10-27
Anem a pitjor, ara sembla que l'ordinador no reconeix el disc dur ("no boot device available"). Quan intente instal.lar des del CD falla perque "no s,ha pogut crear un espai d'intercanvi", ja que "la creació d'espai d'intercanvi a la partició no.5 de SCSI3 (0,0,0) (sda) ha fallat".

Vaig a tornar a passar l,eina de diagnostic, a veure que tal, pero ja ho done per perdut.

---

### Post by traxtorm on 2007-10-27
A veure, per a que es entenem..

Ubuntu té vàries maneres d'anomenar als discs durs, depenent de la connexió.

Si el dispositiu és [IDE/ATA]("http://es.wikipedia.org/wiki/Integrated_Drive_Electronics"), llavors el disc dur s'anomena amb hda, hdb, hdc...

Les connexions IDE són dos: Parallel ATA (és un cable molt gruixut i pla) o SATA (un únic cable, de color roig). Normalment, el lector de CD i el disc dur d'ordinadors vells porten aquest cable. El SATA és el més recent.

Si el dispositiu és[ SCSI]("http://es.wikipedia.org/wiki/SCSI"), llavors el disc dur s'anomena sda, sdb, sdc...


A l'Ubuntu, els discs durs SATA apareixen com si fóssin SCSI (cosa que no és certa), per això si tens un disc amb connexió en SATA, apareixerà com a sda.

També, els pen drives, USB i altres, apareixen com a sda i sdb.




És possible que tingui 5 particions. Segurament deus tenir una partició extesa amb vàries particions lògiques dins.

---

### Post by Ferri on 2007-10-28
Aquest disc té mala pinta. Potser pots intentar, si no ho has fet, fer servir manualment l'eina de linux:
```
fsck -f /dev/sda1
```
Això ho hauràs de fer des d'una live, perquè el disc no pot estar muntat.
Una possibilitat és identificar els sectors defectuosos i, si no són molts o estan relativament propers dins del disc, definir una o més particions que els inclogui, i deixar aquestes particions sense ús. Si la resta del disc està bé igual encara pots aprofitar-ne una bona part.

---

### Post by albello on 2007-10-28
Crec que el sistema ja havia fet servir aquesta eina automaticament quan feia aquest xequeig abans que es carregues ubuntu que us comentava...

He executat el que m'has dit i aquest ha sigut el resultat

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 


Jo no ho entenc.

---

### Post by papapep on 2007-10-28
Bé, el que diu de fet és que tens problemes físics al disc. 

No sé si una altra passada de la eina de Seagate t'ho sol·lucionarà, però segueix pintant com al principi: ves estalviant per un disc nou.

---

