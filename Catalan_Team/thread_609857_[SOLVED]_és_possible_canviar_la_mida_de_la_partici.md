---
title: "[SOLVED] és possible canviar la mida de la partició / ?"
date: 2007-11-11
forum: Catalan Team
---

### Post by xoldy on 2007-11-11
Bona tarda, és possible que pugui ampliar l'espai de la partició / ext3 ?
es que m'he adonat que potser em farà falta ampliar l'espai. El disc dur el tinc dividit en tres parts, la primera és la / on tinc instal·lat el Linux de 40 Gb. després tinc una swap de dues gigues i finalment una FAT32 que tenia sentit quan tenia windows al pc però ara ja no en te tant almenys amb 70 Gb.
es possible guanyar espai? o hauré de refer l'ordi.

Moltes gràcies

---

### Post by papapep on 2007-11-11
Si que és possible. Una altra cosa és que ho tinguis fàcil amb la distribució actual que tens.
No sé fins quin punt la partició FAT t'ho posarà fàcil per a reduïr-la. El particionador que porta el live-cd et pot fer la feina, tot i que també hi ha distros específicament preparades per a fer tasques d'aquestes. Jo he fet servir algun cop la Rescue-CD.
Potser igual ara és el moment adeqüat per aprofitar i passar la /home a una partició independent, no? :-)

---

### Post by xoldy on 2007-11-11
Ja havia pensat en el live cd però em feia por fer-ho sense teràpia de fórum.

Imagino que és molt recomanable tenir la Home a una altre partició oi? Cas de tenir altres particions en quin format és més recomanable enlloc del FAT32?
La carpeta home no es trastoca res si es mou "a sac"= ctrl+x i ctrl+v
Anem aprenent tu.

Moltes gràcies com sempre.

---

### Post by papapep on 2007-11-11
Tenir la /home a banda t'estalvia problemes quan, si et calgués, has de canviar de versió o, fins i tot, si canviessis de distribució.
Qualsevol partició és recomanable tenir-la en EXT3 o qualsevol mode nadiu del kernel de Linux (ReiserFS, XFS, JFS).  Aquí molta gent et podrà aconsellar l'un o l'altre, però en principi l'EXT3 et farà la feina.
El fat32 és un pitafi que van fer els de Redmond i que només serveix per a compartir dades entre equips heterogenis, és un perill potencial a l'hora de conservar la integritat dels fitxers i és nefast a nivell de controlar la dispersió dels fitxers i, per tant, no aprofita massa bé l'espai del que disposa al dispositiu físic.

Després de la perorata, anem a pams:

El que comentes de tallar i enganxar, és per moure tota la /home? Cap a on? A una altra partició? Explica't una miqueta més.

---

### Post by xoldy on 2007-11-11
Si em referia a moure la carpeta home a una altra partició convertiré la fat32 a ext i posaria allà la carpeta home. ho he de fer d'alguna manera especial? o bé copiant enganxant?

---

### Post by papapep on 2007-11-11
Jo no ho faria pas així, amb l'entorn gràfic. 
Hi ha moltes maneres de fer-ho, però potser una interessant és fer servir la ordre **dd**.

Crec que un cop tinguis creada la nova partició i creat el sistema de fitxers ext3, podries fer:

```
dd if=/dev/partició_fat32 of=/dev/nova_partició_ext3
```

crec que amb això et podria funcionar prou bé la còpia.
[B]
Important:[/B] La nova partició ext3 NO ha d'estar muntada quan facis la còpia.
Verifica que funciona correctament la nova partició abans de carregar-te la antiga (mai són poques les precaucions).

---

### Post by xoldy on 2007-11-15
Papapep, no acabo d'entendre la comanda que has escrit. Amb aquesta comanda ja em copia directament la carpeta home a la nova partició?
He trobat [aquestes instruccions]("http://www.ibm.com/developerworks/library/l-partplan.html") per moure la home a una altre partició. Que et sembla?

Moltes gràcies

---

### Post by papapep on 2007-11-15
Pots fer servir el sistema del document d'IBM si et sembla més clar. És una bona manera de fer.ho. 
La ordre "dd" fa una còpia bit a bit. Com ja t'he comentat abans, hi ha unes quantes maneres diferents de fer el mateix.

---

### Post by papapep on 2007-11-15
El que si que hauries de fer és canviar el format de sistema de fitxers, i on diu:

```
2. Create a filesystem on the new partition

To create a filesystem on the new partition, first make sure you know the exact device name for the new partition (for example, /dev/sda5). If you're not sure of the exact device name, stop now and double-check! Then type the following, as root:

# mkfs.ext2 /dev/???
```

hauries de posar:

```
2. Create a filesystem on the new partition

To create a filesystem on the new partition, first make sure you know the exact device name for the new partition (for example, /dev/sda5). If you're not sure of the exact device name, stop now and double-check! Then type the following, as root:

# mkfs.ext**[COLOR="Red"]3[/COLOR]** /dev/???
```

L'ext3 (el sistema de fitxers que fan servir actualment gairebé totes les distros de Linux) és més avançat i segur que el venerable Ext2 que es va fer servir durant molts anys.

---

### Post by xoldy on 2007-11-17
Hola a tothom,
Papapep, estic provant de tot i no m'acaba de funcionar. Abans que res i contradient-me a mi mateix, he fet servir la teva comanda de còpia amb la sentencia *"dd"*, concretament he fet servir la comanda:
```
sudo dd if=/dev/sda1 of=/dev/sda2 
```, on sda1 és el meu sistema de fitxers i sda2, és la nova partició ext3 (abans fat32).
Jo voldria muntar el home a sda2.
El que he aconseguit amb aquesta sentencia és copiar tot el sistema de fitxers en la nova partició. Porto un merdé...
El cas és que vull posar el home a sda2, amb el meu usuari "xoldy" que és la única carpeta d'usuari que tinc al home.
Les qüestions que se'm plantegen son:
[LIST=1]
[*]Com copio el contingut de home a sda2
[*]Com faig per muntar el sda2 com a home, i que em funcioni?
[*]Si la resta no funciona, com torno al punt de partida?
[*]Em faig una mica de por...
[/LIST]
Soc un plom però vull estalviar el pas "fàcil" de reinstal·lar la distro de 0 amb tres particions que sembla que son les més apropiades per treballar només amb Linux. (Conclussió a la que he arribat després d'una vida híbrida de coexistència entre un sistema en el que crec i un sistema que m'han venut...)

Com sempre moltes gràcies

---

### Post by papapep on 2007-11-17
No pateixis home, així és com s'aprèn...:-D

Mira, si en vers de fer:

```
dd if=/dev/particio_N of=/dev/sda2
```

Fas:

```
dd if=/home of=/dev/sda2
```

Copiaràs tot el contingut de /home a /dev/sda2.

Posteriorment, per muntarla, has de modificar el teu /etc/fstab i afegir la línia per muntar la nova /home

Un exemple seria:

> # Entry for /dev/sda6 :
UUID=**[COLOR="Red"]420e5c45-a939-4838-988e-f6bf10197785[/COLOR]** /home ext3 defaults 0 2

El que has d'esbrinar per posar-ho al teu fstab, és el UUID de la teva partició sda2, el qual obtindràs en executar la ordre:

```
sudo vol_id -u /dev/sda2
```

El que et surti, ho fiques en el lloc del UUID (en vermell) del meu exemple i quan hagis desat el nou /etc/fstab i executis la ordre

```
mount -a
```

Et muntarà tots els sistemes de fitxers que hi ha al teu /etc/fstab, inclós el nou /home.

---

### Post by xoldy on 2007-11-18
Moltes gràcies papapep, Seguin els passos del mestre, la cosa ha funcionat. La veritat es que com tot, un necessita temps per anar aprenent coses. Per mi podem donar el fil per tancat.
Una altre cop moltes gràcies pel teu temps

---

### Post by papapep on 2007-11-18
M'alegro que t'hagi funcionat.
Tu  mateix pots donar el fil per resolt.
Clica a Thread Tools i tria "Mark this thread as solved". ;-)

---

