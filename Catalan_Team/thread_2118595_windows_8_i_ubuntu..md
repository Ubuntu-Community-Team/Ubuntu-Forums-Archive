---
title: "windows 8 i ubuntu."
date: 2013-02-21
forum: Catalan Team
---

### Post by gerardrf on 2013-02-21
Bones! Soc nou en aquest foro, perdoneu si faig alguna cosa rara:D.

Ja he vist que hi ha un thread amb un tema similar, pero no he pogut treure gaire suc d'aquest, per això hem disposo a obrir aquest per avere si treiem aigua clara.

Vull apendre a començar a programar pel meu propi peu, i vull fer-ho en ubuntu. He instal·lat ubuntu sobre el windows del meu sobretaula i sobre el notebook de la meva parella (windows 7 els dos), però al instal·lar-lo al meu portatil (windows8) hem dona un error al iniciar-lo un cop ha fet tot el proces d'instal·lació.

Ho he provat amb l'Ubuntu 12.04 i el 12.10 de 32 i 64 bits i res de res. Hem surt aquest avis al intentar engegar-lo "Estado: 0xc000007b.

Ja se que el windows 8 te una bios rara.. pero no  ho he pogut solucionar de cap forma, necesito ajuda...

Moltes gracies!!

---

### Post by wgarcia on 2013-02-22
Has instal·lat Ubuntu a la seva pròpia partició o has utilitzat el programa Wubi dins del propi Windows 8?

---

### Post by gerardrf on 2013-02-22
> **wgarcia said:**
> Has instal·lat Ubuntu a la seva pròpia partició o has utilitzat el programa Wubi dins del propi Windows 8?

De les dos formes i no hi ha manera. Suposo qe sgaura de tocar algo de la bios o instalar ubuntu amb uefi, pero no se com s'hauria de fer ni si aixo es la solucio..

Gracies per contestar!

---

### Post by wgarcia on 2013-02-22
Em sembla que amb Wubi si s'està usant UEFI en comptes de BIOS no es pot instal·lar. 

Amb partició pròpia sí és possible, en aquesta pàgina s'explica en anglès:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Per cert, avui el Linus Torvald, el creador de Linux i encara coordinador del desenvolupament del nucli, parla amb el seu estil sobre el tema aquest del "Secure Boot":

[https://lkml.org/lkml/2013/2/21/228](https://lkml.org/lkml/2013/2/21/228)

---

### Post by gerardrf on 2013-02-25
Ei! Ja ho vaig poder instal·lar, si era seguint els passos anteriors explicats en angles. Pero ara l'he cagat i he esborrat el windows crec, i això que vaig seguir uns tutorials per a fer les particions per ubuntu...

Algú sap com entrar a la bios? Perque quan dono a engegar el portatil directament em surt la pantalla lila de l'ubuntu i no em surt cap pantalla negra dientme el boto que he d'apretar per entrar a la bios ni res, directament lila tot... Desde la bios si que podria recuperar el que he fet... 

Soc un manaces : D

---

### Post by wgarcia on 2013-02-26
Normalment per entrar a la Bios hi ha alguna tecla de funció, F2 o F12, que s'ha de prémer tot just donar-li al botó d'inici de l'ordinador. 

Ara bé, quan dius "he esborrat el Windows", vols dir que no et surt a la "pantalla lila"? (La pantalla lila és un programa que es diu "grub" i que permet escollir entre els diferents sistemes operatius instal·lats a l'ordinador). O és que si que surt però quan l'esculls dóna algun tipus d'error?

Si és el primer cas, que no et surt a la pantalla lila, es pot intentar que el "grub" reconegui el windows abans de fer cap altra cosa. 

Si és que dóna un error llavors sí que potser s'hagi de fer alguna cosa amb el Windows, recuperació o reinstal·lació, tot i que en aquest cas s'haurà de prendre en compte que l'instal·lador de Windows passa de tot i esborra els sectors d'arrencada. L'Ubuntu continuarà allí, perquè el Windows no veu la partició on està Linux, però no es podrà arrencar. Però no és massa problema perquè el que s'ha de fer és el que se explica en aquest altre enllaç, en cas que es reinstal·li o es recuperi Windows un cop instal·lat Linux:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

