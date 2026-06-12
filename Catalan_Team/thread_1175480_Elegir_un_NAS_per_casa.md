---
title: "Elegir un NAS per casa"
date: 2009-06-01
forum: Catalan Team
---

### Post by akyra on 2009-06-01
Hola a tothom.

Estic plantejant-me compar una unitat NAS per utilitzar a casa, i bàsicament per poder fer copies de seguretat de tots els documents digitals que tinc (fotos, metges, etc.), pràcticament tot el que és necessaria ho escanejo i ho guardo.
Ja tinc un disc dur multimedia en xarxa de 1TB i voldria poder tenir copies de respaldo de tot el que és important.

He començat a mirar per internet i realment no sé que s'ha de tenir en compte o mirar a l'hora d'elegir-ne un.

Que vol dir RAID 0, RAID 1, què s'ha de considerar, es millor agafar un mini ordinador barato i de baix consum...., etc.

Bé voldria saber les vostes experiencies i les coses a tenir en compte.

Moltes gracies.

---

### Post by papapep on 2009-06-01
Ufff..resposta complicada.

Podries començar per [aquí]("http://ca.wikipedia.org/wiki/RAID").

Després podries concretar quin espai necessites tenir disponible, de quin pressupost, quina mena de fitxers vols salvaguardar, si serà un recurs bàsicament de lectura o s'actualitzarà sovint (lectura/escriptura)....

Doncs el que et deia, que la resposta es planteja fàcilment, però la resposta no ho és gaire :)

---

### Post by PatrickVogeli on 2009-06-01
Com ha dit el papapep, es un tema molt ampli.

Jo et puc parlar de 2 amb els quals tinc certa experiencia:

[Linksys NAS200]("http://www-es.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=ES%2FLayout&cid=1175237981158&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8115892870B01")

[Dlink DNS-323]("http://www.dlink.es/cs/Satellite?c=Product_C&childpagename=DLinkEurope-ES%2FDLProductCarousel&cid=1197319419075&p=1197357768092&packedargs=ParentPageID%3D1197337625381%26TopLevelPageProduct%3DBusiness%26locale%3D1195806681347%26packedargs%3DProductParentID%253D1197318673191&pagename=DLinkEurope-ES%2FDLWrapper")

D'aquest 2, el dlink el tenim a la feina, servint bàsicament per a accés FTP. Es molt complert, i el discs es formatejen en ext2 (o ext3, no recordo ara mateix) i, per tant, no tenen el limit de 4gb per arxiu. El fet que sigui ext2 li es igual a windows, no has d'afegir cap driver ni res, llegeix/escriu igual que un pendrive o el que sigui. A més, conserva permisos i tot això, cosa que igual t'es util. Té bastantes opcions i es pot configurar tot via web si no m'equivoco.

El linksys no et puc dir massa cosa, però té molt bona pinta, a més de ser bastant economic (em sembla que l'he venut a menys de 150&#8364;). Inclou 2 ports usb on hi pots connectar un pen drive si fes falta i en general em va agradar. Però realment no se com funciona ni com formateja els discos ni res, només tinc una impressió general. També es configura via web.

salut

---

### Post by akyra on 2009-06-02
Hola

El tipus d'arxiu serien bàsicament fotos familiars (ara totes són digitals i les voldria tenir guardades a dos llocs) que es van afegint de forma regular, cada 15 dies, reculls de DVD's familiars i després documents oficials, metges, etc.

El pressupost no ho he plantejat, però veig que hi ha diferents preus i molt variats, des dels 250€ + els hdd fins a 700€ o més.

Jo crec que amb un D-link que he vist [http://www.dlink.com/ads/?theURL=L3Byb2R1Y3RzLz9waWQ9NTA5&adID=ad_dns323_0207]("http://www.dlink.com/ads/?theURL=L3Byb2R1Y3RzLz9waWQ9NTA5&adID=ad_dns323_0207"), o alguna cosa similar faria prou.

Ara tot ho tinc guardat amb un disc dur multimedia de 1TB (tamany més que suficient actualment, en un futur suposo que també) amb accés per xarxa que també té ftp i client de bittorrent, el problema és que com el disc dur s'espatlli... molt malament. Mentrestant ho tinc guardat en un altre disc dur usb.

El que m'agradaria és que es puguessin fer copies o sincronitzacions de les carpetes de forma automàtica i que si un dia s'espatlla un no em poses a plorar perquè he perdut els documents de molts anys.

Més que res, es que no sé que haig de considerar per comprar-ne un, a part de la capacitat del disc i la connexió de xarxa.

Gracies

---

### Post by papapep on 2009-06-02
Doncs així jo ho montaria amb un procés al cron que llencés un rsync que sincronitzés cada n temps els dos discs (o els directoris que tu vulguis dels discs) i a córrer, que són dos dies :)

---

### Post by PatrickVogeli on 2009-06-02
per aixo que comentes, trobo que t'aniria de conya montar-los en raid 1 (mirall), cosa que amb el dlink aquest que has posat pots fer sense problemes. Així estaràs bastant cobert i no et caldra sincronitzar res.

---

### Post by akyra on 2009-06-02
Si papapep, això sembla collonut, quan decideixi comprar-ho, que serà segurament cap a finals d'any, ja preguntaré com fer-ho amb el cron.

Com veus no són dades crítiques que estiguin canviant a cada moment, sino que és un ús molt més domèstic.

També crec que podria posar les màquines virtuals que ocupen molt d'espai i les utilitzo poc, no sé que tal aniran...

Crec que també és important l'accés de forma segura des de la xarxa. El hdd multimedia que tinc té servidor ftp però la seguretat és mínima i no l'utilitzu.

Per cert, es pot fer amb Cron, si el que vull es copiar d'un disc dur de xarxa a un altre?

Gracies.

---

### Post by akyra on 2009-06-02
El que tua has dit el NAS200 també té molt bona pinta, i he vist que fa copies automàtiques, que tal funciona això.

Com podria fer copies d'un altre disc dur extern?

Disculpe-ho la ignorància.

---

### Post by papapep on 2009-06-02
PatrickVogeli:
> per aixo que comentes, trobo que t'aniria de conya montar-los en raid 1 (mirall), cosa que amb el dlink aquest que has posat pots fer sense problemes. Així estaràs bastant cobert i no et caldra sincronitzar res.

No confonguem: RAID _no_ equival a còpia de seguretat...més d'un ha picat en això i ha tingut molts mals de panxa després....

Akyra:
> Per cert, es pot fer amb Cron, si el que vull es copiar d'un disc dur de xarxa a un altre?


Es pot fer el que et faci falta, això és Linux :D 
La única limitació que pots tenir depenent del que signifiqui "d'una xarxa a un altre", és d'ample de banda, però això no té a veure amb el sistema de còpia.

---

### Post by akyra on 2009-06-03
Hola papapep

L'ample de banda no em preocupa gaire per el volum de dades que haig de moure una vegada feta la primera copia, més que res vull tenir les dades guardades en varios llocs, seria el mateix que faig ara, agafar un disc dur extern USB i quan m'en recordo vaig copiant coses, amb el perill que la meva dóna hagi guardat coses i no m'ho hagi dit i per tant no ho copii, o que jo no me'n recordi.

El que vull és tenir-ho en varis llocs, i en cas de que un disc dur es faci malbé, que algun dia pasarà, que ho tingui en un altre lloc.

Salutacions

---

