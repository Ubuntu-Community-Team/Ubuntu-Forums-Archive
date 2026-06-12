---
title: "Error als repositoris"
date: 2009-06-10
forum: Catalan Team
---

### Post by simfomet on 2009-06-10
Hola a tots,

    després d'un canvi de pc he tornat a instal·lar Ubuntu i després d'actualitzar repositoris hem surt aquest missatge:

W: Error del GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 6AF0E1940624A220
W: Error del GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY A3CD88794B2C459E

És perillós en algun sentit? Què puc fer perquè no hem surti?

D'altra banda he instal·lat amule 2.2.5 i voldria compartir crédits entre emule i amule. Googlejant he trobat una manera però la primera instrucció que hem diu que fiqui a la consola es cd ~/.aMule i en aquesta ordre ja hem dóna un error i surt que no troba el directori. A què es deu? Que puc fer per solventar-ho?

Gràcies.

---

### Post by papapep on 2009-06-10
Si fas una consulta al fòrum, veuràs que s'ha preguntat altres cops:

[http://ubuntuforums.org/search.php?searchid=60395417](http://ubuntuforums.org/search.php?searchid=60395417)

---

### Post by oriolsbd on 2009-06-10
Noés perillós.

Simplement, has activat alguns repositoris de Launchpad i no tens la clau pública per a poder-les llegir. A "Sistema>Administració>Fonts de programari", pestanya "Programari de tercers" les pots veure. Mira que aquests repositoris realment t'interessin (segurament sí). Et passo un enllaç on diuen com baixar aquestes claus públiques:
[http://alliberats.cat/gpg-error-del-launchpad/](http://alliberats.cat/gpg-error-del-launchpad/)

Salut!

---

### Post by simfomet on 2009-06-10
papapep alguna de les solucions que dóna a l'enllaç fa referència a desinstal·lar els paquets a través de synaptic i no voldria treure aquests programes ja que els faig anar.

Oriolbd el que entenc en l'enllaç és que dóna una manera que no surti el missatge però les claus públiques seguiré sense tenir-les.

Alguna idea respecte l'amule?

Gràcies.

---

### Post by torracastanyes on 2009-06-10
Per a l'amule, potser això et pot servir:

[http://www.amule.org/amule/index.php?PHPSESSID=1393f28060c6b1b174419d9756c03c87&topic=15927.0](http://www.amule.org/amule/index.php?PHPSESSID=1393f28060c6b1b174419d9756c03c87&topic=15927.0)

---

### Post by oriolsbd on 2009-06-10
Hola de nou.

Amb les instruccions que jo et passava ja t'instal·lava les claus públiques. Si t'hi fixes, l'última sentència conté un "apt-key add". :-)

---

### Post by papapep on 2009-06-11
Simfomet: no sé què has llegit exactament dels enllaços que et vaig passar, però només era per a que entenguessis que només et cal importar les claus gpg dels repositoris en concret, i que no és un problema "per se", sinó més com un tema de seguretat i tranquilitat per a tu de la autenticitat del creador del paquet.
Per la resta, el que et comenta l'oriolbsd és correcte.

I, simfomet, un fil per a cada tema, si us plau, no barregem coses.

---

### Post by simfomet on 2009-06-11
Gracies pels vostres consells papapep i oriolsbd, ho he pogut solventar. I perdona papapep però vaig amb peus de plom amb el món linux-ubuntu que un va aprenent poc a poc i fa cagades de principiant.

Pel que fa a l'amule obriré un altre fil si a cas.

---

