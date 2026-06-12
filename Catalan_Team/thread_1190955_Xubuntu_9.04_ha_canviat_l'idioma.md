---
title: "Xubuntu 9.04 ha canviat l'idioma"
date: 2009-06-18
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-06-18
Bones. M'explico.
No se com, tot sovint tinc tot l'escriptori en anglès.
He verificat al suport d'idioma (ara language suport!) que està marcat Catalan; Valencian (Andorra).
He fet correr Update Manager i m'ha donat els següents errors:

E: linux-image-2.6.28-13-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.28-13-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

algú pot ajudar-me, sisplau.
gracies.

---

### Post by RainCT on 2009-06-18
Ves a la terminal i fes un ```
sudo aptitude full-upgrade
``` i a continuació també ```
sudo dpkg --configure -a
```, i copia'ns la sortida de les dues ordres.

---

### Post by Miquel Ubuntero on 2009-06-19
Hola RainCT.
He fet el que m'has dit.
En reinicar pc, si intento entrar amb kernerl 2.6.28-13 hem surt aquest error: Kernel Panic. Unable to mount root fs on unknow-block.
Amb 2.6.28-11 si que puc entrar però continua tot en anglès.
Per cert, he oblidat de anotar el que sortia al terminal, sap greu.
Puc fer quelcom més?
i gracies.

---

### Post by oriolsbd on 2009-06-19
El kernel 2.6.28-13 a mi també em dóna problemes en un dels meus PCs (en l'altre no). En el que em dóna problemes, entro amb la versió anterior (2.6.28-12).

Pel tema de l'idioma, no et puc ajudar massa, però no crec que tingui res a veure amb el kernel. Per cert, què vols dir amb "tot sovint"? Et surt en anglès només alguns cops?

---

### Post by Miquel Ubuntero on 2009-06-19
Hola Oriol.
No hem vaig expressar be. Hem passa  sempre, continuadament que tinc l'idioma malament.
Salut!

---

### Post by oriolsbd on 2009-06-19
Ens pots passar què et respon la comanda següent?
```
locale
```

Salut!

---

### Post by Miquel Ubuntero on 2009-06-20
i tant que puc!
aquí ho tens:
miquel@miquel-laptop:~$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ca_AD.UTF-8
LC_CTYPE="ca_AD.UTF-8"
LC_NUMERIC="ca_AD.UTF-8"
LC_TIME="ca_AD.UTF-8"
LC_COLLATE="ca_AD.UTF-8"
LC_MONETARY="ca_AD.UTF-8"
LC_MESSAGES="ca_AD.UTF-8"
LC_PAPER="ca_AD.UTF-8"
LC_NAME="ca_AD.UTF-8"
LC_ADDRESS="ca_AD.UTF-8"
LC_TELEPHONE="ca_AD.UTF-8"
LC_MEASUREMENT="ca_AD.UTF-8"
LC_IDENTIFICATION="ca_AD.UTF-8"
LC_ALL=

Salut!

---

### Post by Miquel Ubuntero on 2009-06-20
Hola de nou.
No se si pot ajudar aquesta informació, però en iniciar k3b hem diu que hi ha un error de sistema. Enganxo el que diu:

"El joc de caràcters local del vostre sistema (és a dir, el joc de caràcters emprat per codificar noms de fitxer) és ANSI_X3.4-1968. És altament improbable que això hagi estat intencionat. Segurament el vostre joc de caràcters local ni tan sols està definit. Un valor incorrecte donarà problemes a l'hora de crear projectes de dades.
Solució: Per tal d'establir adequadament el joc de caràcters local, assegureu-vos que les variables d'entorn LC_* estan definides. Normalment les eines de configuració de les distribucions ja se'n fan càrrec."

Salut!

---

### Post by oriolsbd on 2009-06-21
Hola, Miquel.

L'error que et retorna el "locale" quan et diu "locale: Cannot set LC_ALL to default locale: No such file or directory" és una mica estrany, i crec que pot venir d'aquí.

Prova dues coses més. D'una banda, executa la comanda:
```
locale -a
```

Això et mostra tots els idiomes que tens instal·lats. A veure si et surt el ca_AD.utf-8.

Una altra cosa que pots provar és executar algun programa que se't vegi en anglès forçant-li un locale en català diferent del ca_AD (per veure si amb un altre sí que et funciona. Per exemple, podries provar d'executar:
```
LANG=ca_ES.UTF-8;firefox
```
Si amb el ca_ES se't veu bé, és que tens algun problema amb el ca_AD. En aquest cas, activa't el "Catalan;Valencian (Espanya)". Jo és el que tinc activat.

Una altra cosa que pots mirar és, al suport d'idioma, anar al botó "Instal·la/suprimeix llengües..." (com a mínim a Gnome s'hi va així, a XFCE no sé com va), anar a l'idioma català i mirar que tinguis activat tant les traduccions bàsiques com les avançades.

Salut!

---

### Post by Miquel Ubuntero on 2009-06-22
Hola a tots.
El tema del suport d'idioma tampoc hem funcionaba. Donat que he tingut varios problemes ja fa uns quants dies he decidit tirar pel dret i he formatat el disc dur i m'he tornat a posar el Xubuntu 8.10 que hem funcionabe de molt be.
disculpeu la meva poca pacinecia ;)
i moltes gracies a tots, de moment ara hem va tot be.
Salut!

---

