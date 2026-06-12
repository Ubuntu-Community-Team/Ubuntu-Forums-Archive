---
title: "seguretat, &quot;virus&quot; o d'altres"
date: 2009-08-26
forum: Catalan Team
---

### Post by egin on 2009-08-26
bones,

Espero que aquesta pregunta no sigui gaire repetida, però la veritat sento bastants opinions i cap que m'aclareixi de veritat.

El que em preocupa és la seguretat, ja que no tinc instal·lat cap "antivirus" (entenen el terme com un programa que vetlla per la seguretat de les dades i integritat del sistema) ni cap tallafocs.
M'han comentat que ubuntu incorpora un tallafocs d'origen però no se com es gestiona, ni si està actiu.

La meva pregunta és si cal algun programari d'aquestes característiques o per contra si actualitzant el sistema quan toca no calen extres de seguretat.

En una de les meves paranoies sobre això, em va venir al cap el fet de que si el sistema és lliure i el codi el pot llegir qualsevol, també el fa més vulnerable a possibles "enganys" mal intencionats del sistema per fer-lo rebel·lar dades o actuar sense el nostre consentiment.

Espero que em pugueu treure de dubtes.

Gràcies i de nou, felicitats pel fòrum que en català encara hi ha poca cosa per internet.

---

### Post by pauelmaco on 2009-08-26
> **egin said:**
> 
El que em preocupa és la seguretat, ja que no tinc instal·lat cap "antivirus" (entenen el terme com un programa que vetlla per la seguretat de les dades i integritat del sistema) ni cap tallafocs.
M'han comentat que ubuntu incorpora un tallafocs d'origen però no se com es gestiona, ni si està actiu.

La meva pregunta és si cal algun programari d'aquestes característiques o per contra si actualitzant el sistema quan toca no calen extres de seguretat.

Un antivirus en linux, l'únic que fa és evitar que sense voler infectis a un usuari de winbug$ quan li envies un document o així, l'ubuntu mai se t'infectarà. Tot i això, no està de més tenir el tallafocs configurat.

> **egin said:**
> 
En una de les meves paranoies sobre això, em va venir al cap el fet de que si el sistema és lliure i el codi el pot llegir qualsevol, també el fa més vulnerable a possibles "enganys" mal intencionats del sistema per fer-lo rebel·lar dades o actuar sense el nostre consentiment.


Justament això el fa més segur, ja que hi ha més gent que en pot trobar els errors, els pot entendre i corregir. D'aquesta manera, tots els usuaris poden arreglar errors de manera que n'hi queden pocs sense veure. A sobre, Ubuntu no incorpora cap mena de software de seguiment ni res similar, ja que això cantradiuria (es diu així?) la llicència GPL.

Espero haber-te aclarit els dubtes.

Adéu

---

### Post by papapep on 2009-08-26
Respecte el tema dels antivirus, no és que [Gnu/Linux]("http://ca.wikipedia.org/wiki/GNU/Linux") sigui perfecte i invulnerable (no existeix el sistema perfecte), però, per ara i tant, es beneficia de dues característiques que té:

 * A diferència "d'altres" sistemes operatius, Gnu/Linux (hereder de part de la filosifia [Unix]("http://ca.wikipedia.org/wiki/Unix")), està orientat a ser un sistema operatiu de xarxa i amb una estructura enfocada a la seguretat i l'estabilitat. Tot i així no és impossible fer un virus que n'ataqui vulnerabilitats. El complicat és assolir fer-ne un que pugui fer gaires estralls. La seva concepció, sempre que l'usuari no es dediqui a fer bestieses, minimitza els possibles efectes del codi maliciós que intenti atacar-lo. La separació dels espais d'execució d'usuari respecte els de sistema, l'[estructura rígida i clara de permisos]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Permisos") complica considerablement infiltrar-se en un d'aquests sistemes. Els únics intents que s'han arribat a conéixer de certa entitat, han estat els [rootkits]("http://es.wikipedia.org/wiki/Rootkit"), però sense gaire incidència.

Del que comentes del codi, tal i com et comenta en Pauelmaco, el fet de que el codi sigui obert i visible al món té dues vertents. Una que es poden trobar maneres per a "fer trampa", però la segona és que igual que tu pots ficar codi maliciós dins d'un programa, tothom (que en sàpiga) ho podrà veure que el codi hi és, i solucionar-ho.
En el món del programari de font tancada (privatiu) mai saps què hi ha dins, et poden fer, ja m'entendreu, el que vulguis. Tinc molt i molt clar quina opció és més segura :)

Respecte els tallafocs, quantes més portes tingui casa vostra més possibilitats hi ha de que per alguna us entrin a robar, oi? Aleshores, si les amaguem (hi posem un tallafocs i tanquem tots els serveis innecessaris) minimitzem les possibilitats de ser atacats. 

Els sistemes *nix (Unix, Gnu/Linux) empren com a tallafocs una eina de nom [iptables]("http://ca.wikipedia.org/wiki/Iptables"), terríblement eficient i potent però, també, certament críptica per als no iniciats (i a cops, fins i tot, pels iniciats). Ubuntu té un programa, [ufw]("http://packages.ubuntu.com/jaunty/ufw"), (Uncomplicated FireWall - Tallafocs sense complicacions) que tot i que per sota segueix emprant l'iptables (si funciona bé, i ho fa, per a què reinventar la roda?), però que hi afegeix una capa que en facilita l'ús, simplificant la sintaxi. A més, pels més novells, o pels que no es volen trencar massa la closca, també hi ha una eina gràfica de nom [gufw]("http://packages.ubuntu.com/jaunty/gufw") que encara ho fa més senzill.
Com sempre, al món del programari lliure el que no falta són opcions :)

I sí, aquesta és una pregunta reiterada en el temps, pel qual en faré un apunt al wiki de l'equip per no haver de repetir cada cop el totxo :D

Espero haver-me sapigut explicar.

---

### Post by torracastanyes on 2009-08-27
Només un detall més per acabar de rematar:

Com ja has dit tú mateix, al treballar amb codi obert, qualsevol pot modificar un programa per convertir-lo en un troià i penjar-lo a la xarxa en qualsevol lloc, i fins que algú no el revisi, s'adoni de la trampa i ho arregli, pot haver caçat uns quant passarells.

El que resulta força més complicat, i a això es refereix en papapep, i es un dels avantatges de Linux sobre "d'altres", és poder "colar" el programa modificat en un repositori oficial sence que ningú se n'adoni.

Per això, avans de baixar qualsevol programa d'internet, val la pena plantejar-se si hi ha alguna raó de pes que ens obligui a util.litzar aquella versió en concret, en lloc de la del repositori o la pàgina oficial.

---

