---
title: "Remastersys o programes semblants?"
date: 2010-02-23
forum: Catalan Team
---

### Post by mrc2407 on 2010-02-23
Hola de nou.

Per qüestions de feina necessito instal·lar Ubuntu en molts ordinadors diferents, tots amb els mateixos programes i paquets. He estat mirant una mica, i suposo que el més fàcil és crear un LiveCD de la meva instal·lació, però tampoc sé per on començar. He trobat Remastersys ([http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)), que sembla que fa bé la seva feina, però hi ha coses que no acabo d'entendre: si faig servir l'opció **dist**, que sembla que és la que necessito, quan instal·li aquest LiveCD en altres ordinadors podré crear els usuaris principals com els necessiti, no? Vull dir cada ordinador ab la seva pròpia contrasenya.

Algú ha hagut de fer servir algun programa semblant?

---

### Post by kukat on 2010-02-23
Jo crec que és el programari indicat. Jo el vaig utilitzar una vegada per a crear un live cd i em va anar de meravella. Però no he provat d'instal.lar-ho en cap ordinador. 
Lo de la contrasenya no crec que hi haja cap problema, mentre tingues la de root....

---

### Post by papapep on 2010-02-23
Ubuntu té una eina que es diu [UCK]("http://uck.sourceforge.net/") (Ubuntu Costumization Kit), i l'Orestes en va fer [un manual molt interessant]("http://bazaar.launchpad.net/%7Eubuntu.cat/ubuntaires/manual-UCK/revision/21/manual_ca.pdf") que explicava les passes que s'han d'efectuar.

---

### Post by SiscoGarcia on 2010-02-23
> **papapep said:**
> [...] l'Orestes en va fer [un manual molt interessant]("http://bazaar.launchpad.net/%7Eubuntu.cat/ubuntaires/manual-UCK/revision/21/manual_ca.pdf") que explicava les passes que s'han d'efectuar.

Em sembla que l'enllaç que has posat no apunta al document pdf per descarregar, en canvi [aquest]("http://bazaar.launchpad.net/%7Eubuntu.cat/ubuntaires/manual-UCK/download/orestes%40tsc.upc.edu-20081107195129-ri38khlo7k7pi6db/manual_ca.pdf-20081107195042-dr26p34gopswxocc-1/manual_ca.pdf") sí que m'ha funcionat.

---

### Post by mrc2407 on 2010-02-23
SiscoGarcia, papapep: Moltes gràcies per l'ajuda, però no sé ben bé si això és el que necessito. Per exemple, voldria fer servir OpenOffice 3.2 i Firefox 3.6 (que no estan inclosos en Ubuntu 9.10), i del Firefox 3.6 m'agradaria canviar, per exemple, la pàgina d'inici o els motors de cerca, i això no sé com ho podria fer a través de la terminal.

De tota manera, se m'acudeix que puc combinar els dos procediments, és a dir, fer servir Remastersys per a generar la ISO de la meva instal·lació actual i llavors extreure paquests innecessaris amb l'UCK. Es podria, o necessito una ISO amb l'Ubuntu original per a fer servir l'UCK?

---

### Post by wgarcia on 2010-02-24
Per instal·lar programari que encara no està en la versió actual hi ha tres vies. La primera és habilitar el dipòsits "backport", però això sols actualitza alguns programes molt estables, per exemple OpenOffice.org 3.2 no te l'instal·laria. 

La segona és buscar el corresponent PPA (Personal Package Archives), que sí que inclou les últimes versions, i es va actualitzant a mesura que els desenvolupadors van introduint correccions d'errors. El problema que té és que no està assegurat que no hi hagi errors i inestabilitats en les diferents versions que es van baixant. 

La tercera és anar als llocs de cada programa (per exemple a OpenOffice.org) i baixar-se el paquet "deb" corresponent si n'hi ha. L'avantatge que té és que si es tracta d'una versió estable que s'ha alliberat hauria de funcionar bé, el desavantatge és que no és un paquet de dipòsits Ubuntu i per tant no seguirà les actualitzacions automàtiques.

---

