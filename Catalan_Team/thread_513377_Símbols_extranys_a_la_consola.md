---
title: "Símbols extranys a la consola"
date: 2007-07-30
forum: Catalan Team
---

### Post by benetj on 2007-07-30
Hola companys

Volia demanar-vos si sabeu com solventar aquest problema.
Quan estic en mode consola on toca haver-hi una vocal accentuada o amb diéresi, c trencada etc ... surt un símbol extrany.

Algú me sabria dir com arreglar-ho?

Gràcies.

---

### Post by papapep on 2007-07-31
Comprova que a Sistema>Administració>Suport d'idioma tinguis instal·lat el català, i habilita'l com a idioma per defecte.

---

### Post by patrickfromspain on 2007-07-31
es un bug. sudo setupcon i despres ja va be. 

Salut!

---

### Post by benetj on 2007-07-31
Hola amics, gràcies per contestar.
Però el problema el tenc a les tty no en el terminal gràfic.

En el gràfic es veu perfecte.

Seguiré investigant.

Salut!

---

### Post by papapep on 2007-07-31
> Hola amics, gràcies per contestar.
Però el problema el tenc a les tty no en el terminal gràfic.


Bé, però ja has provat el que t'ha dit en patrick???

---

### Post by benetj on 2007-08-01
Hola papapep perdona,

no ho havia comentat, doncs si ho he executat però segueix el tema igual.

Salutacions.

---

### Post by guillemsola on 2007-08-02
Hola, respecte això dels accents, desde la consola si escrius 

```
locale
```

que és el que et diu?
jo ho tinc tot a ca_ES.UTF-8 i no tinc problemes

```
LANG=ca_ES.UTF-8
LANGUAGE=ca_ES:ca:en_GB:en
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC="ca_ES.UTF-8"
LC_TIME="ca_ES.UTF-8"
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY="ca_ES.UTF-8"
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER="ca_ES.UTF-8"
LC_NAME="ca_ES.UTF-8"
LC_ADDRESS="ca_ES.UTF-8"
LC_TELEPHONE="ca_ES.UTF-8"
LC_MEASUREMENT="ca_ES.UTF-8"
LC_IDENTIFICATION="ca_ES.UTF-8"
LC_ALL=
```


si no has de fer un 

```
dpkg-reconfigure locale
```

i selecciona el ca_ES.UTF-8

Això senzillament executa un programa on has de triar un idioma i la seva codificació de la llista. Fixa't en quin "locale" tenies al principi si ho vols deixar tot igual després de trastejar.

A veure si et serveix...

Salut!

---

### Post by benetj on 2007-08-02
hola angrychai, gràcies per contestar, mira t'explico:

la sortida de locale me surt tal com així:
```
LANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMLANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMERIC="ca_ES.UTF-8@valencia"
LC_TIME="ca_ES.UTF-8@valencia"
LC_COLLATE="ca_ES.UTF-8@valencia"
LC_MONETARY="ca_ES.UTF-8@valencia"
LC_MESSAGES="ca_ES.UTF-8@valencia"
LC_PAPER="ca_ES.UTF-8@valencia"/
LC_NAME="ca_ES.UTF-8@valencia"
LC_ADDRESS="ca_ES.UTF-8@valencia"
LC_TELEPHONE="ca_ES.UTF-8@valencia"
LC_MEASUREMENT="ca_ES.UTF-8@valencia"
LC_IDENTIFICATION="ca_ES.UTF-8@valencia"
LC_ALL=

```

Intento instal·lar el paquet locale i no existeix, però crec que es el locales que s'ha d'instal·lar, de fet li tenc, i quan reconfiguro veig que fa un update de les locale que tenc al sistema:
```
Generating locales...
  ca_AD.UTF-8... up-to-date
  ca_ES.UTF-8... up-to-date
  ca_ES.UTF-8@valencia... up-to-date
  ca_FR.UTF-8... up-to-date
  ca_IT.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
```

Podria ser un bug de les locale   ca_ES.UTF-8@valencia?
Com puc canviar-la a ca_ES.UTF-8 de tota la vida?

Salut!

---

### Post by guillemsola on 2007-08-06
que més podem fer...

per canviar l'idioma del locale edita el fitxer /etc/environment

un cat del meu:

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="ca_ES.UTF-8"
LANGUAGE="ca_ES:ca:en_GB:en"

canvia el que hi ha a LANG per el locale que vulguis. Després només et fa falta re-iniciar la sessió "ctrl+alt+backSp" i fes el locale des de consola i tindràs el seleccionat a environment.

Els locales disponibles es troben a /var/lib/locales/supported.d
Allí hi tens un arxiu per cada idioma i a dins els locales suportats. Si n'has d'afegir un després hauras de fer el dpkg-reconfigure locales.

Espero que amb això aconsegueixis solucionar-ho.

Salut!

---

