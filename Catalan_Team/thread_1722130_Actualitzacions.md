---
title: "Actualitzacions"
date: 2011-04-05
forum: Catalan Team
---

### Post by Arteazul on 2011-04-05
Hola a tots,
des de fa un parell de dies, em surt un cartellet al panell amb un signe d'interrogació al mig, que em diu que les actualitzacions automàtiques no funcionen, que hauré de fer-les manualment. Li done a fer-ho manualment i em surt el següent problema:

Se ha producido un error GPG: [http://repository.spotify.com](http://repository.spotify.com) stable Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 4F9946354E9CFF4ENo s'ha pogut obtenir [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz) 404 Not Found


Podeu ajudar-me? Moltes gràcies :)

---

### Post by kukat on 2011-04-05
Aixó es un problema dels repositoris. Hauràs afegit el repositori de l'Spotify però no li has indicat quina és la clau d'eixe repositori. 

Amb açò crec que s'arreglarà, si ho copies i enganxes a la terminal: 

gpg --keyserver wwwkeys.de.pgp.net --recv-keys 4E9CFF4E
gpg --export 4E9CFF4E |sudo apt-key add -
 

;)

---

### Post by Arteazul on 2011-04-05
> **kukat said:**
> Aixó es un problema dels repositoris. Hauràs afegit el repositori de l'Spotify però no li has indicat quina és la clau d'eixe repositori. 

Amb açò crec que s'arreglarà, si ho copies i enganxes a la terminal: 

gpg --keyserver wwwkeys.de.pgp.net --recv-keys 4E9CFF4E
gpg --export 4E9CFF4E |sudo apt-key add -
 

;)

Joder, doncs no ha funcionat, no, quina ràbia. Lo pitjor es que no m'instal·la noves actualitzacions amb aquest problemeta...

---

### Post by wgarcia on 2011-04-06
Prova el programet següent, que et baixa totes les claus que falten. Des d'una terminal:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys

I després també des d'una terminal:

sudo launchpad-getkeys

---

