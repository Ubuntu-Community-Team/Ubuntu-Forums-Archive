---
title: "NTFS i linux"
date: 2009-03-25
forum: Catalan Team
---

### Post by Haliotis on 2009-03-25
Hola, aquest cop no és un problema ben bé, és més aviat per aprendre.
M'agradaria tenir una partició de disc per a dades que pugui veure des de linux-ubuntu 8.10 i des de Windows vista (sí...:$ venia amb el portatil... i no està de més, de moment, mentre aprenc amb linux).
La qüestiço és que smepre he pensat que aquesta partició hauria de ser NTFS o FAT32... I em decanto per la NTFS...
però al linux no li agrada aquesta partició, té un munt de restriccions a poder fer en una partició ntfs.
La pregunta és perquè?
i l'altre pregunta és, si la partició fos FAT 32 quina avantatges i desavantatges tindria?
ale els que tingueu idees compartiu_les.
Gràcies

Max

---

### Post by SiscoGarcia on 2009-03-25
> **Haliotis said:**
> ale els que tingueu idees compartiu_les.

Se m'acut la idea de cercar per google a veure què, i la primera opció que em dóna a l'entrada [fat32]("http://www.google.es/search?q=fat32&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a") és de la [viquipèdia en espanyol]("http://es.wikipedia.org/wiki/FAT"); passa el mateix pera a [ntfs]("http://www.google.es/search?q=ntfs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a"), que també em remet a la mateixa [viquipèdia]("http://es.wikipedia.org/wiki/NTFS").

A partir d'aquí, i tenint en compte [tot plegat]("http://www.gnulinux.cat/windows/") jo tinc clar què faria.

---

### Post by Haliotis on 2009-03-26
gràcies per la resposta... però...
el tema de mantenir windows al portatil é sper una qüestió pràctica (ja que el tinc, no em sobra, i hi ha alguns drivers que tinc millor configurats a windows que a linux.. per una qüestió d'aprenentetge, ho sé.. però mentre aprenc, no molesta) i per una qüestió de garantia...
però deixant de banda això, que no era el tema que volia parlar.. :P (pq estic d'acord, bàsicament :D) entenc les diferèncie sentre FAT i NTFS, peo pq linux no pot treballar còmodament amb NTFS?
Merci :)
Max

---

### Post by papapep on 2009-03-26
Potser per que és una tecnologia propietària i tancada de Microsoft?? :)

---

### Post by albandy on 2009-03-26
No hauries de tenir cap problema en fer o accedir a particions NTFS, la qüestió és que tinguis el paquet ntfsprogs instal·lat

---

### Post by SiscoGarcia on 2009-03-26
> **Haliotis said:**
>  pq linux no pot treballar còmodament amb NTFS?

Com ja t'ha respost papapep el problema és que és "propietat" de Microsoft, i Linux treballa més còmodament amb altres formats de fitxers, nadius o no. Tot i això, com apunta albandy, hi ha possibilitat de treballar-hi però fent esforços afegits que has de valorar si surten a compte.

---

### Post by albandy on 2009-03-26
collons un altre lleidatà. XD

---

### Post by SiscoGarcia on 2009-03-26
> **albandy said:**
> collons un altre lleidatà. XD

Ja t'havia vist fa uns dies per aquí. Per on pares? Jo per Pardinyes.

Compte que estem segrestant el fil ;)

---

### Post by albandy on 2009-03-26
zona alta. I ja no dic res mes que això de rebentar fils no mola.

---

### Post by marteljorge on 2009-03-29
> **Haliotis said:**
> gràcies per la resposta... però...
el tema de mantenir windows al portatil é sper una qüestió pràctica (ja que el tinc, no em sobra, i hi ha alguns drivers que tinc millor configurats a windows que a linux.. per una qüestió d'aprenentetge, ho sé.. però mentre aprenc, no molesta) i per una qüestió de garantia...
però deixant de banda això, que no era el tema que volia parlar.. :P (pq estic d'acord, bàsicament :D) entenc les diferèncie sentre FAT i NTFS, peo pq linux no pot treballar còmodament amb NTFS?
Merci :)
Max

Hi ha un projecte per intentar solucionar els problemes. Copypaste from gnu.org:

Application:  	Ext2 File System Driver for Windows
Replaces: 	NTFS, FAT32 filesystems
URL: 	[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

The Ext2 file system driver for Windows allows you to access Ext2 and Ext3 file systems developed for the Linux kernel. Thus, you can easily read data from your own or your friend's GNU/Linux computers on a Windows system.

Espero que sigui útil.

---

