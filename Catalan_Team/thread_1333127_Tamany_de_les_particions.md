---
title: "Tamany de les particions"
date: 2009-11-21
forum: Catalan Team
---

### Post by Leirdalag on 2009-11-21
Hola a tots!
Seguint els consells que vaig rebre per aquest fòrum, em disposo a instal·lar l'ubuntu desde 0 ara que ja he realitzat una copia de seguretat de tots els meus fitxers personals. Només em sorgeix un dubte que no acabo de trobar ben explicat. A l'hora de fer les particions de forma manual, quantes hauria d'haver?de quin tipus i de quin tamany?No es millor fer una instal·lació standard?

En el meu cas disposo d'un disc dur d'1 TB al que accedeixen 4 usuaris i només vull tenir instalat l'ubuntu.
Gràcies!

---

### Post by PatrickVogeli on 2009-11-21
Jo el que faria es una particio de 15gb per a /, una swap igual de gran que la teva ram i la resta, una particio per /home

salut

---

### Post by Leirdalag on 2009-11-21
Gràcies pel consell!
De totes maneres, algú em sabria dir d'algun tutorial on s'expliqui aquest punt de la instalació?es que crec que deu ser millor especificar-ho de forma manual,no?la instalació standard quines particions fa?
Respecte al tamany que dius que hauria de tenir la partició swap hi ha molta informació contradicctoria a internet.

---

### Post by Rubunter on 2009-11-21
Així ho faria jo

/boot 156 MB
/ no el faria mes gran que 10GB
El swap 512MB, suposant que tens força RAM
/home la resta


És només una idea. Modifica-ho segons les necessitats. Hi ha tutorials a tot arreu.

---

### Post by Leirdalag on 2009-11-21
Tinc 3 o 4GB de Ram, no ho tinc clar. De moment tinc Windows Vista i no s'aclara, depen d'on ho consulti em diu 3 o 4 xD

---

### Post by jdk9 on 2009-11-21
> **Leirdalag said:**
> Tinc 3 o 4GB de Ram, no ho tinc clar. De moment tinc Windows Vista i no s'aclara, depen d'on ho consulti em diu 3 o 4 xD

Mmm de principi, instal·la't la versió de 64 bits. I deus tenir 4 Gb, suposo, el que passa és que probablement tens el Vista de 32 bits i no te'n reconeix més.
Jo el que faria és el que ha dit en PatrickVogeli (Tot i que / la faria en format ext4, la swap de 4Gb i la /home en format fat32). 

Salut!

---

### Post by papapep on 2009-11-21
> Tot i que / la faria en format ext4, la swap de 4Gb i la /home en format fat32)

Aquest consell, i ho dic de bon rotllo, és una bestiesa. El format FAT32 és antic, inestable i perillós a no poder més. Tenir la /home amb FAT32 és opositar al desastre. Si algú ho té i se n'ha sortit, enhorabona, però és temerari de pebrots, i es carrega tot el sentit de fer servir GNU/Linux per la seva estabilitat i seguretat.

La swap de 4 Gb, tot i que pot ser opinable, és massa gran. Si la arriba a fer anar serà insofrible i seria símptoma de que alguna cosa va realment malament al sistema. Amb 2 Gb hauria de ser més que suficient.

A partir d'aquí, aquest tema sempre crea allaus de comentaris contradictoris, Leirdalag, però segur que en el terme mig trobaràs un bon consell pel que demanes.

Una partició arrel de 15-30 Gb (per què quedar-se curt si tens un TB de disc??), i la resta pot ser tranquilament /home (i els 2 Gb per la partició d'intercanvi).

[Aquí]("http://sclipo.com/videos/view/instalar-ubuntu-avanzado-personalizar-particionado") tens un vídeo que igual t'ajuda a veure com es fa.

---

### Post by jdk9 on 2009-11-21
> **papapep said:**
> Aquest consell, i ho dic de bon rotllo, és una bestiesa. El format FAT32 és antic, inestable i perillós a no poder més. Tenir la /home amb FAT32 és opositar al desastre. Si algú ho té i se n'ha sortit, enhorabona, però és temerari de pebrots, i es carrega tot el sentit de fer servir GNU/Linux per la seva estabilitat i seguretat.

La swap de 4 Gb, tot i que pot ser opinable, és massa gran. Si la arriba a fer anar serà insofrible i seria símptoma de que alguna cosa va realment malament al sistema. Amb 2 Gb hauria de ser més que suficient.

Jo la /home ho tinc així perquè sinó no m'agafa els fitxers el Windows (el problema d'usar programes que per desgràcia no funcionen a Linux o no saber sincronitzar el reproductor de música amb Linux :S)

I la swap la tinc del doble de memòria ram que hi tinc (la tinc de 4Gb), no sé qui m'ho va dir i com que no sé massa com va l'swap, ho he deixat així per costum.

El pròxim cop que reinstal·li Ubuntu, ja ho faré tal com dius, la veritat és que soc ignorant amb certes coses (fa com a molt 1 any i mig que m'he passat), com ara per exemple amb el fat32. 

Gràcies!

---

### Post by Rubunter on 2009-11-21
Jo tinc 3GB de RAM i mai he arribat a fer servir el swap, així que per mi els 512 són més que suficient. Com he dit, això depèn de les necessitats de cadascú.

---

### Post by Leirdalag on 2009-11-21
Ok!
Gràcies a tots, seguint els vostres consells finalment ho he aconseguit. He dedicat al directori arrel 30GB, 2GB per a la swap i la resta per a /home.

---

### Post by ifanlo on 2009-11-22
Ei, jdk9!

> **jdk9 said:**
> Jo la /home ho tinc així perquè sinó no m'agafa els fitxers el Windows (el problema d'usar programes que per desgràcia no funcionen a Linux o no saber sincronitzar el reproductor de música amb Linux :S)

Segur que ningú t'havia dit que existia l'"Ext2 Installable File System For Windows": [http://www.fs-driver.org/](http://www.fs-driver.org/)

És molt pràctic, però un xic insegur, doncs posa tot el sistema d'arxius del Linux (ext2 o ext3) a disposició del Windows.

Però, per descomptat, millor solució que tenir el /home amb FAT. ;-)

Salut,

---

### Post by PatrickVogeli on 2009-11-22
la /home en fat32? L'instal·lador t'ho deixa fer? I els enllaços simbòlics? I els atributs de seguretat?

Jo em pensava que donaria error si ho provaves.. i de fet ho trobó tan brutal que quasi s'hauria de considerar com un bug que t'ho permeti fer.

salut

---

### Post by jdk9 on 2009-11-22
> **ifanlo said:**
> Ei, jdk9!



Segur que ningú t'havia dit que existia l'"Ext2 Installable File System For Windows": [http://www.fs-driver.org/](http://www.fs-driver.org/)

És molt pràctic, però un xic insegur, doncs posa tot el sistema d'arxius del Linux (ext2 o ext3) a disposició del Windows.

Però, per descomptat, millor solució que tenir el /home amb FAT. ;-)

Salut,

Mmmm pot ser interessant, ja ho provaré!

> **PatrickVogeli said:**
> la /home en fat32? L'instal·lador t'ho deixa fer? I els enllaços simbòlics? I els atributs de seguretat?

Jo em pensava que donaria error si ho provaves.. i de fet ho trobó tan brutal que quasi s'hauria de considerar com un bug que t'ho permeti fer.

salut

Vaig fer trampa, ho vaig copiar manualment jo després :$

---

### Post by somhi on 2009-11-22
Algú ha comentat el fet de fer una partició específica per a /boot.

Voldria saber els avantatges i inconvenients que això comporta.

Gràcies,
Jordi

---

### Post by Rubunter on 2009-11-22
> **somhi said:**
> Algú ha comentat el fet de fer una partició específica per a /boot.

Voldria saber els avantatges i inconvenients que això comporta.

Gràcies,
Jordi

Una d'elles és que si fas dual o triple boot i per qualsevol motiu et carregues la partició d'ubuntu, amb ella et carregues el grub i per tant deixes de poder arrancar l'altre SO. A més, si fas dual boot amb un altre Linux pots tenir un únic boot pels dos. També si vols encriptar el / necessites el boot en una altra partició. S'ha discutit en molts fòrums sobre la utilitat de fer el /boot a part. Jo el tinc a part, tot i que ara ja no faig dual boot, però mai se sap.

---

### Post by akyra on 2009-11-23
Estic d'acord amb les particions d'en Patrick.
També estic d'acord amb el que diu Papapep de no utilitzar fat32, de fet dius que vols instal·lar només ubuntu, jo per tant en el /home utilitzaria "ext4" i respecte a la memoria swap, em sembla que quan hivernes l'ordinador, et guarda el que tens a memòria dins de la partició swap. Sí és així la partició de swap hauria de ser del mateix tamany que la memoria RAM de l'ordinador, encara que és molt estrany que en funcionament normal utilitzi 4G de swap.

No sé si algú pot confirmar això de l'hibernació.

Salutacions.

---

### Post by Pablitus on 2009-11-24
Hola,

> Segur que ningú t'havia dit que existia l'"Ext2 Installable File System For Windows": [http://www.fs-driver.org/](http://www.fs-driver.org/)

A mi l'fs.driver em va donar molts problemes, no l'aconsellaria. Ara no sé com va perquè ha desaparegut el Windows del meu disc dur.

Sobre compartir boot entre dues distros o instal·lacions:
> A més, si fas dual boot amb un altre Linux pots tenir un únic boot pels dos

Vair llegir un article on deia que això no es pot fer. Hi deia: "Así mismo, no puedes compartir una partición /boot (el problema es que muchas distribuciones sobreescribirán tu partición /boot cuando las instales." Jo no en tinc ni idea i em vai creure el que s'hi deia, potser tenint algunes coses en compte si que es pot fer. [Enllaç a l'article en qüestió]("http://eddiedean.wordpress.com/2008/03/15/multiarranque-en-linux/") sobre multi-arrencada en GNU/Linux.

Fins ara.
Pau

---

