---
title: "[SOLVED] versió en català"
date: 2007-09-22
forum: Catalan Team
---

### Post by lpargemi on 2007-09-22
Hola

Una pregunta de molt baix nivell:

Quina és la darrera versió en català i on es por trobar?

He descarregat el Kubuntu, i encara que trii el català com a idioma predeterminat, només s'instal.la en anglès. (hi ha una opció en castellà, però ho borra sense contemplacions al no ser l'opció per defecte, i no sé ni com restaurar-ho). 

Per altra banda, com que sóc nou amb l'assumpte, m'és igual començar per un escriptori que un altre. Això si, voldria poder-hi muntar un servidor apache per fer proves amb pàgines Web.

He mirat de busca al Catalan LoCo Team aquesta informació (quina és la darrera versió traduïda) i en la meva inutilitat he estat incapaç de trobar-ho.

Agraït per l'interès

Lluís

---

### Post by papapep on 2007-09-22
Tinc dues notícies per a tu, una bona i una dolenta:

La dolenta és que no has abandonat el Catalan LoCo Team aquest fòrum n'és una altra expresió. ;-)

La bona és que símplement instal·les la versió que et plagui d'Ubuntu (amb gnome o kde) i posteriorment li configures l'idioma que et plagui (p. ex. el català).

Aquí en pots trobar referències de com fer-ho:

[http://ubuntuforums.org/showthread.php?t=443585&highlight=idioma](http://ubuntuforums.org/showthread.php?t=443585&highlight=idioma)
[http://ubuntuforums.org/showthread.php?t=387775&highlight=idioma](http://ubuntuforums.org/showthread.php?t=387775&highlight=idioma)

Salutacions i benvingut a la comunitat (que no és la de l'anell :-D)

---

### Post by orestesmas on 2007-09-22
Jo afegiria que, si vols un CD ja en català "d'entrada", el LoCo Team també s'encarrega de fer-lo. Concretament, jo vaig fer el de la Kubuntu 7.04 quan va sortir a l'abril. Pots baixar-te la imatge de Caliu, per exemple:
[http://caliu.cat/blog/2007/04/20/la-ubuntu-704-feisty-en-catala-al-servidor-de-caliu/](http://caliu.cat/blog/2007/04/20/la-ubuntu-704-feisty-en-catala-al-servidor-de-caliu/)

Però jo gairebé m'esperaria, si pots, al 20 d'octubre que sortirà la propera versió.

Que la disfrutis

---

### Post by lpargemi on 2007-09-23
Hola

Gràcies per la vostra resposta.

De moment he baixat i instal.lat la versió 7.04 en catalànglish, i fins ara no he aconseguit vagi això del Wireless. 

Ja aniré depurant l'assumpte amb els enllaços que m'heu passat.

Agraït

Lluís 

PD. Orestes: Jo em segueixo apuntant al curset de pares a l'escola!

---

### Post by papapep on 2007-09-23
Per si no estaves al cas, el proper 20 d'octubre serem a Olot. Si t'hi acostes segur que podrem solventar els teus problemes (informàtics, eh!! ;-))

Per a més informació: [https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy](https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy)

---

### Post by lpargemi on 2007-09-24
Gràcies per la informació.

Finalment això ha funcionat

Envio aquestes línies per si hi ha algú tan passerell com jo que li cal. (De fet el login passerell ja estava agafat, però és el que m'escau a mi).

Seguint els consells de les línies de dalt el què cal és descarregar qualsevol versió, i instal.lar-lo amb l'opció de què l'idioma per defecte sigui el català.

L'altre sarau és aconseguir que vagi Internet. La cosa anava per wifi,  i per més que ho provés el sistema no es va entendre amb servidor DHCP (que és qui dona les adreces IP que permeten identificar l'ordinador a la xarxa interna de casa). La solució salomònica és introuir l'adreça IP a mà, així com ladreça d'enllaç i les DNS d'enllaç. Oli en un llum

Després d'això encara gairebé tot surt en anglès, però tal com comenta en Papapep només cal anar i canviar l'idioma. Lúnic problema és que el suport per català no surt a la llista.

Per tant el pas previ és actualitzar la instal.lació perquè hi sigui.

Bé senyors passerells: resulta que a l'Ubuntu hi ha una utilitat que fa la recerca i instal.lació d'aquests programes tota sola: 

[INDENT]A la pestanya Applications (encara estem en anglès) hi ha a la última l'opció **Add/Remove Applications,** que és la bona. 

Hi apareix una llista de programes i paquets immensa, i el què cal fer (després d'haver introduït el password) és seleccionar el Language support i demanar d'instal.lar-lo. Resulta que Ubuntu sap on anar a buscar aquestes coses. (estan en una cosa anomenada repositoris).

Després de què ho instal.lis vas a la pestanya  "System" i busques el Language Support. Ara si que pots triar el català (i treure l'anglès?). Després de fer-ho va a buscar més programes a més repositoris, i després de tot això ja funcina.

I si no va, haureu de fer el que es comenta als enllaços de més amunt. (a mi em va funcionar)  
[/INDENT]

Bé, després d'apallissar-vos us agraeixol'atenció que m'heu prestat, i també agraeixo als que porteu això que hagiu aconseguit que funcioni.

Lluís

---

### Post by CarlesOriol on 2007-09-25
El teu post és una mica extrany.

> Després d'això encara gairebé tot surt en anglès, però tal com comenta en Papapep només cal anar i canviar l'idioma. Lúnic problema és que el suport per català no surt a la llista.

Si que surt. He insta&#320;lat un munt d'ubuntus en 32 i 64 bits i sempre surt. No he vist MAI que no hi fos.

per tant:

> A la pestanya Applications (encara estem en anglès) hi ha a la última l'opció Add/Remove Applications, que és la bona.

Hi apareix una llista de programes i paquets immensa, i el què cal fer (després d'haver introduït el password) és seleccionar el Language support i demanar d'instal.lar-lo. Resulta que Ubuntu sap on anar a buscar aquestes coses. (estan en una cosa anomenada repositoris).

no té sentit fer-ho. Pots anar directament al darrer punt.

---

