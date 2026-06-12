---
title: "Problema amb KpackageKit"
date: 2011-04-02
forum: Catalan Team
---

### Post by Lomarc on 2011-04-02
Hola, tinc un problema amb les actualitzacions de les aplicacions..., i es que al apretar el botó de "comprova si hi ha actualitzacions" em dona un error, i em surt una finestra amb el següent missatge
```
No es pot obtenir el bloqueig exclusiu sobre el gestor de paquets.
Si us plau, tanqueu totes les eines de gestió de paquets que puguin estar executant-se
I als detalls:
p, li { white-space: pre-wrap; } W: GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
E: Error http://ppa.launchpad.net maverick/main Sources
404 Not Found

```Us deixo una captura de pantalla també
[IMG]https://lh6.googleusercontent.com/_ONeVQ21m5dE/TZfYGmVIwQI/AAAAAAAALdk/AwBRJcvi5SE/instant%C3%A0nia2.png[/IMG]


Espero que em pugueu ajudar... gràcies!

---

### Post by wgarcia on 2011-04-03
Tens com el missatge diu, tancades totes les altres aplicacions d'actualització? Pes exemple el Gestor de Paquetes Synaptic o el Centre de programari ubuntu?

---

### Post by albert-I on 2011-04-03
o un terminal obert amb el aptitude o el apt-get.

---

### Post by Lomarc on 2011-04-23
> **albert-I said:**
> o un terminal obert amb el aptitude o el apt-get.


Perdó a tots, he tingut uns problemes personal i tècnics i m'avia oblidat completament del fil aquest!!!

Jo crec que ni tinc res més obert, l'únic que faig, es engegar el pc, anar a actualitzacions, actualitzar i quant esta al 99% em dona l'error...
Abans ho feina igual i no em donava cap error...

---

### Post by wgarcia on 2011-04-24
Pel que diu a la tercera línia comptant des de baix, pot ser que falti alguna signatura per autentificar els paquets. 

Mira si el que es diu en aquest missatge:

[http://ubuntuforums.org/showpost.php?p=10500462&postcount=5](http://ubuntuforums.org/showpost.php?p=10500462&postcount=5)

t'ho arregla.

---

### Post by pepitu on 2011-04-24
Bé, no sé si és la millor manera de fer-ho, però si instal·les el synaptic i actualitzes des d'allà, tot torna a la normalitat, almenys a mi em va funcionar. i no recordo si fins i tot fent un 'sudo apt-get update' des de la consola també es podia solucionar.


salut!

---

