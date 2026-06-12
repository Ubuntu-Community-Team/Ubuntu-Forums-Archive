---
title: "No puc accedir a l'ordinador"
date: 2009-11-30
forum: Catalan Team
---

### Post by auska1714 on 2009-11-30
Ei! 

aviam si em podeu ajudar, no se perquè des de dissabte al vespre que al intentar iniciar el meu ordinador, el qual tenia configurat per tal d'accedir directament a l'escriptori, m'apareix la finestra on he d'introduir l'usuari i la contrasenya. I en fer-ho torna a carregar la mateixa finestra i així indefinidament. Que puc fer per arreglar-ho, ja que hi tinc informació que m'interessaria molt no perdre ja que la necessito per l'institut. I per tant, m'interessa no formatjar el disc dur. 

L'ordinador té instal·lat l'ubuntu 9.10

Moltes gràcies,

Salut!

---

### Post by oriolsbd on 2009-11-30
Molts cops, és per culpa de falta d'espai en alguna partició. Entra-hi en mode terminal (des del menú on et demana l'usuari hi deu haver una opció per a fer-ho), i executa la comanda següent:
```
df -m
```

Mira si hi ha alguna partició plena. Una altra opció és entrar amb un LiveCD i mirar si falta espai en alguna partició.

Salut!

---

### Post by Black_02 on 2009-11-30
Hola,
pots arrencar des de el cd de Ubuntu (aquest no et demanarà contrasenya).

Però si no et deixa entrar es perquè escrius malament el teu nom (l'has de escriure tot en minúscules) o be escrius malament la teva contrasenya (crec que diferencia majúscules de minúscules) i pensa que si és un numero has d'activar el control numèric del teclat.

De totes formes, si això no resulta, arranca del cd de instal.lació de Ubuntu (Live CD), d'allí podràs navegar pel disc dur i copiar la informació a un pendrive o a un altre lloc. 

Sort!!

---

### Post by auska1714 on 2009-11-30
> **oriolsbd said:**
> Molts cops, és per culpa de falta d'espai en alguna partició. Entra-hi en mode terminal (des del menú on et demana l'usuari hi deu haver una opció per a fer-ho), i executa la comanda següent:
```
df -m
```

Mira si hi ha alguna partició plena. Una altra opció és entrar amb un LiveCD i mirar si falta espai en alguna partició.

Salut!

Es provable que sigui això, ja que el tenia molt pler. Però no trobo la opció per accedir-hi des del terminal. Algú que tingui el karmic instal·lat em pot dir com es fa, per poder eliminar arxius des d'allà?

Salut!

---

### Post by auska1714 on 2009-11-30
Val, ja he pogut entrar al terminal i al executar la comanda df -m, tal com has dit em surt:

S. fitxers     Blocs    1M    En ús    Lliures    %Ús    Muntat a /dev/sda1
                     109786   85025      19185    82%    /
udev                    501        1       501     1%    /dev
none                    501        1       501     1%    /dev/shm
none                    501        1       501     1%    /var/run
none                    501        0       501     0%    /var/lock
none                    501        0       501     0%    /lib/init/rw

aviam que...

Salut!

-----------------------------
**He intentat instal·lar de nou el gnome, per veure si el problema venia d'una modificació de la configuració d'aquest. Però tampoc funciona... Cap altre idea?**

---

