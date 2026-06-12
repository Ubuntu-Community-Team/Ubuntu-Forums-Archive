---
title: "el grub no funciona"
date: 2009-03-12
forum: Catalan Team
---

### Post by Josep-Sanz on 2009-03-12
Hola.

He instal·lat l'Ubuntu al meu ordinador amb la versió "alternate".
S'ha fet tota la instal·lació correctament, però quan engego l'ordinador es carrega directament el windows xp. El grub no apareix. És com si no hagués instal·lat res.
És estrany perquè en l'últim pas de la instal·lació es detecta que hi ha un sistema operatiu instal·lat (windows xp), em pregunta si vull que instal·li el grup en el sector d'arrencada del primer disc dur (li dic que si), i em demana que tregui el cd d'instal·lació per a reiniciar el sistema. És a dir, que ho fa tot aparentment bé, però quan engego l'ordinador no apareix el grub per cap lloc.

Em podeu ajudar sisplau?

Salut!

---

### Post by albandy on 2009-03-12
Has instal·lat l'ubuntu en un altre disc dur o al mateix? Al propi alternate cd tens una opció de recuperació.

---

### Post by kukat on 2009-03-12
Prova el SuperGrub Disk
[http://forjamari.linex.org/frs/?group_id=61&release_id=499](http://forjamari.linex.org/frs/?group_id=61&release_id=499)

És un CD (o un executable sobre windows) que arregla el Grub en molts casos (com per exemple en la reinsta&#320;lació de Window$. 
Ocupa 5MB com a màxim, i es altament recomanable tindre'l a mà per a quan hi haja problemes per culpa de Window$ o per problemes com el teu....

Es prou intuïtiu, no crec que tingues problemes.

EDITO: a més a més està en català

---

### Post by Josep-Sanz on 2009-03-13
> **albandy said:**
> Has instal·lat l'ubuntu en un altre disc dur o al mateix? Al propi alternate cd tens una opció de recuperació.

Gràcies.
L'he instal·lat en un altre disc dur.
Si. He vist que al disc alternate hi ha una opció de recuperació. Encara no l'he mirada, però suposo que aquesta opció servirà per a recuperar quan hi ha hagut un problema en la instal·lació. Però és que aquest no és el meu cas. La instal·lació la va fer perfecta. L'únic que passa és que el grub no apareix quan engego l'ordinador. Carrega directament el windows xp. És com si no hagués instal·lat l'Ubuntu. Com si no hagués fet res.
Provaré primer el que m'ha dit kukat.
Ja us contaré.

---

### Post by Josep-Sanz on 2009-03-13
> **kukat said:**
> Prova el SuperGrub Disk
[http://forjamari.linex.org/frs/?group_id=61&release_id=499](http://forjamari.linex.org/frs/?group_id=61&release_id=499)

És un CD (o un executable sobre windows) que arregla el Grub en molts casos (com per exemple en la reinsta&#320;lació de Window$. 
Ocupa 5MB com a màxim, i es altament recomanable tindre'l a mà per a quan hi haja problemes per culpa de Window$ o per problemes com el teu....

Es prou intuïtiu, no crec que tingues problemes.

EDITO: a més a més està en català

Gràcies kukat.

Ets del poble d'Enric Valor?
Provaré el supergrub disk.
Ja et contaré com m'ha anat.

Salut!

---

### Post by albandy on 2009-03-13
> **Josep-Sanz said:**
> Gràcies.
L'he instal·lat en un altre disc dur.
Si. He vist que al disc alternate hi ha una opció de recuperació. Encara no l'he mirada, però suposo que aquesta opció servirà per a recuperar quan hi ha hagut un problema en la instal·lació. Però és que aquest no és el meu cas. La instal·lació la va fer perfecta. L'únic que passa és que el grub no apareix quan engego l'ordinador. Carrega directament el windows xp. És com si no hagués instal·lat l'Ubuntu. Com si no hagués fet res.
Provaré primer el que m'ha dit kukat.
Ja us contaré.

No serà un disc USB ? Suposant que no ho sigui, tal com t'he commentat al cd alternate hi ha una opció de recuperació. Un cop entres tens la opció de regenerar el GRUB

---

### Post by oriolsbd on 2009-03-13
Suposo que et refereixes a un altre disc dur, i no a una altra partició del mateix disc dur, oi?

En aquest cas, és possible que no t'arranqui el Grub perquè el deus haver instal·lat en el sector d'arranc del segon disc, mentre que el teu ordinador arranca des del primer. Pots comprovar si és així entrant a les opcions d'arranc de la teva Bios, i dient-li que arranqui des del segon disc dur.

És a dir, es pot instal·lar Ubuntu al disc (o a la partició) que es vulgui. Però si vols que a l'arranc del sistema et reconegui el teu Grub, has d'instal·lar-lo al sector d'arranc del teu disc dur principal (aquell que llegeix per defecte el teu ordinador quan arranca).

Si és això, tens diverses opcions:
- Des de les opcions d'arranc de la Bios del teu ordinador, indicar-li que arrenqui per defecte a partir del segon disc dur. No crec que sigui la millor opció, perquè si més endavant tornes a instal·lar qualsevol sistema operatiu hauràs de recordar que el disc dur que arrenca el teu ordinador és el segon.
- Reinstal·lar el Grub en el primer disc dur. No sé com es fa, però segur que algú per aquí et pot ajudar. :-)   Crec que és la millor opció.
- Reinstal·lar tot Ubuntu en el disc dur/partició que vulguis, però tenint en compte d'instal·lar el Grub en el primer disc dur.  Tampoc no és una mala opció, però serà una mica més llarga que la segona, i ja has reinstal·lat diversos cops Ubuntu en poc temps.

Segur que hi ha més opcions, però ara mateix no hi caic. :-)

Abans de fer res, comprova el que t'he dit d'arrancar un cop l'ordinador des del segon disc dur, a veure si et reconeix el Grub.

Salut!

---

### Post by kukat on 2009-03-15
Si, Castalla és el poble d'Enric Valor!i Cassana també (que ve a ser el mateix) jejej :D

Doncs prova el que diu l'Oriol, jo també instal.laria el grub en el primer disc dur (en el que vullges que administre el grub). 

Amb el supergrub disk que t'he dit pots indicar-li que el grub estiga al disc dur que vulgues. Personalment veig que és millor fer-ho a mà (l'edició del grub) però el supergrub disk es senzill i útil per a fallades o coses com aquesta.

Salut!

---

### Post by Josep-Sanz on 2009-03-18
Hola.

He instal·lat el supergrub. Ja em deixa triar si vull engegar amb l'ubuntu o amb el windows xp. Però ara tinc el mateix problema que vaig plantejar en un missatge anterior que vaig enviar al fòrum anomenat "l'ubuntu no engega en un amd athlon": comença a carregar però arriba un moment que s'atura i ja no continua. En l'anterior missatge em van dir que sospitaven de la targeta gràfica perquè era molt rara, i em van suggerir enviar-li un paràmetre en la càrrega que fos "vga=791". Ho he fet però s'atura igual.
Ja no sé què fer.
Està vist que hi ha una força superior que no vol que instal·li l'ubuntu en el meu ordinador.
Per favor, em podeu ajudar?
Gràcies.

---

### Post by Josep-Sanz on 2009-04-06
Ja ho he solucionat.
El problema era, efectivament com algú m'havia dit, la targeta gràfica.
Feia servir la que estava integrada a la placa base.
Vaig posar una que tenia per ahí connectada al port AGP i s'acabaren els problemes. Ara l'Ubuntu ja engega perfectament.
Gràcies a tots.

---

### Post by MorlanXaos on 2009-05-18
He tingut els mateix, problema després de re-instal·lar el XP. He provat el supergrub i ha funcionat molt be cap problema. Sols que no proveu de utilitzar la opció de ajuda (en català), ja que despres de moltes i confuses pantalles per recuperar el grub, l'ordinador s'ha quedat rumiant per molta estona. Finalment he fet un reset, he carregat el CD una altre vegada i he selecionat la 4 opció que apareix en el primer menú "GRUB=>MBR&LINUX AUTO", i ja està. (En el cas de tenir el grub en el primer disc dur)

---

