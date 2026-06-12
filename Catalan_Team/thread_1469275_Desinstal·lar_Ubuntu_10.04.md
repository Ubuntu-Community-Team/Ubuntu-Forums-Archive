---
title: "Desinstal·lar Ubuntu 10.04"
date: 2010-05-02
forum: Catalan Team
---

### Post by lluisalguero on 2010-05-02
Hola nois,
no us penseu malament, no he renegat de Linux :lolflag:

A causa d'aquest problema ([http://ubuntuforums.org/showthread.php?t=1468224](http://ubuntuforums.org/showthread.php?t=1468224)) vaig intentar instal·lar la 10.04, pensant que em sobreescriuria la 10.04 que no em funcionava, i no va ser així, es va instal·lar com si fos un 3er sistema operatiu.
Ara el que voldria fer és treure aquesta instància de la 10.04 que a hores d'ara no faré servir, ja que he pogut solventar els problemes que tenia amb l'anterior.

Moltes gràcies de nou per la vostra ajuda

Lluís

---

### Post by SiscoGarcia on 2010-05-02
Hola Lluís,

A part que amb entrades com aquesta

> **lluisalguero said:**
> Hola nois,

estàs limitant la capacitat de resposta perquè les noies que puguin ajudar-te a resoldre el problema no et respondran ;) jo el que faria és:

1.- Fer còpia de totes les dades que vulguis conservar, per si de cas.
2.- Assegurar-te bé quina partició és la que vols eliminar.
3.- Amb el gparted, o equivalent, eliminar-la i passar-li aquest espai a la partició que vulguis (potser l'anterior 10.04).
4.- Armar-te de paciència i esperar que acabi el procés... i que acabi bé.
5.- Tornar a repensar el [problema anterior]("http://ubuntuforums.org/showthread.php?t=1468224").

---

### Post by wgarcia on 2010-05-02
Jo afegiria, un cop eliminada la partició no desitjada i reassignat l'espai, des de la instal·lació que et funciona fer:
sudo grub-update 

per actualitzar l'arrencada del grub sense la partició incorrecta. 

I un cop actualitzat el grub instal·lar-lo on correspongui, amb 

sudo grub-install <disc-on-està-el-grub>

perquè quedin les opcions d'arrencada correctes al grub en iniciar l'ordinador.

---

### Post by lluisalguero on 2010-05-02
Gracies a tots dos

provarem això que em dieu i ja us faré 5 cèntims

---

### Post by lluisalguero on 2010-05-03
He fet una captura del gparted, us la ensenyo perquè no voldria fer res malbé, a veure si em podeu orientar una mica

Com puc saber quina és la partició que estic fent servir?

Suposo que també, apart d'eliminar una de les dos particions sda5/sda7 també tindria que fer el mateix amb sda6/sda8, no?

Aquestes 2 particions de 1 Mb deuen ser alguna cosa?

Moltes gràcies pel vostre ajut

Lluís

---

### Post by akyra on 2010-05-03
La partició que arranca ara el sistema operatiu és la sda5, és la que tens el punt de muntatge "/" a la sda7 no hi tens res. Per cert la partició "/" és inmensa per un sistema operatiu d'ubuntu, amb una de com a molt amb una 20GB faries més que suficient.

La primera de 1MB que tens, normalment la utilitza windows per fer l'arranc, però si no la tens assignada tampoc valdria per res, mirar si al gestor de particions de windows et dóna alguna dada, però diria que no val per res, 
Les dues particions que no tens assignades, una de 1MB i l'altre de 4MB, no hi tens res i per tant és espai que podries reutilitzar, o millor, per deixar una mica més neta la taula departicions.
També tens 2 swap que podries eliminar-ne un.
De fet si mires el gparted, pots veure com tens una clau posada, això vol dir que les que tens muntades són la "sda5" i "sda6"

Un dubte a on tens la teva partició /HOME ?

No has plantajat tornar-ho a refer de nou, i deixar la partició de windows, que suposo que et cal, i tornar a refer les de linux?

Adeu

---

### Post by lluisalguero on 2010-05-03
> **akyra said:**
> La partició que arranca ara el sistema operatiu és la sda5, és la que tens el punt de muntatge "/" a la sda7 no hi tens res. Per cert la partició "/" és inmensa per un sistema operatiu d'ubuntu, amb una de com a molt amb una 20GB faries més que suficient.

La primera de 1MB que tens, normalment la utilitza windows per fer l'arranc, però si no la tens assignada tampoc valdria per res, mirar si al gestor de particions de windows et dóna alguna dada, però diria que no val per res, 
Les dues particions que no tens assignades, una de 1MB i l'altre de 4MB, no hi tens res i per tant és espai que podries reutilitzar, o millor, per deixar una mica més neta la taula departicions.
També tens 2 swap que podries eliminar-ne un.
De fet si mires el gparted, pots veure com tens una clau posada, això vol dir que les que tens muntades són la "sda5" i "sda6"

Un dubte a on tens la teva partició /HOME ?

No has plantajat tornar-ho a refer de nou, i deixar la partició de windows, que suposo que et cal, i tornar a refer les de linux?

Adeu

Llavors haig d'entendre que les que hi ha una clau són les que estic utilitzant actualment, no? les altres dues són les que tindria que esborrar.

Entenc que amb 20Gb seria suficient per a l'Ubuntu, tots els programes, documents, etc, que tinc i/o tindré?

lo de la partició /HOME la tinc (crec) a la mateixa partició on tinc instal·lat l'Ubuntu. No sé si això és el que et refereixes.

Gràcies pel teu ajut
Lluís

---

### Post by lluisalguero on 2010-05-04
Ja ho tinc solucionat, després de fer una copia de seguretat de les coses importants, des de el Vista m'he carregat les particions i he començat de cap i de nou.

Moltes gràcies a tots per l'ajut

---

### Post by akyra on 2010-05-04
Hola Lluis, una aclaració.
20GB em refereixo al sistema operatiu. Els documents, projectes, etc, teus es guarden dins del teu "/HOME/usuari", i l'espai dependrà del que tu facis servir. Jo per exemple tinc 20GB per "/" (el sistema operatiu) 4GB per "swap" i 200GB per "/home"
que és a on carregarè amb dades.

Salutacions.

---

### Post by lluisalguero on 2010-05-04
> **akyra said:**
> Hola Lluis, una aclaració.
20GB em refereixo al sistema operatiu. Els documents, projectes, etc, teus es guarden dins del teu "/HOME/usuari", i l'espai dependrà del que tu facis servir. Jo per exemple tinc 20GB per "/" (el sistema operatiu) 4GB per "swap" i 200GB per "/home"
que és a on carregarè amb dades.

Salutacions.

Gràcies per la resposta. Alguna cosa pareguda he llegit per aquests mons d'internet.

Ara ho tinc tot junt, és possible separar-ho tal i com ho tens tu?

---

### Post by akyra on 2010-05-06
Jo ho faria, crec que és importantissim si vols anar actualitzant l'ubuntu.

Hauries de fer de nou la taula de particions, però tot just has començat no seria gaire traumàtic.

Entenc que tens en una partició windows, i en una altre ubuntu (/,home) oi?
Si es així, hauries d'arrancar el live CD d'instal·lació d'ubuntu i quan anar per instal·lar-lo de nou. Quan et demani a on ho vols fer (veuràs la taula de particions) dir que ho vols partir manualment, i t'apareixerà el teu disc dur amb les particions actuals.
Pots pasar una captura de pantalla de gparted per veure com tens actualment les particions, i a on ho voldries fer, aniria molt bé per guiar-te i no trencar res.

Una vegada saps a on ho vols, només es qüestió d'anar fent particions, indicar el punt de montatge i el sistema de fitxers (jo ho tinc amb ext4, crec que actualment és el que toca)

Ja diràs alguna cosa.

Adeu

---

### Post by lluisalguero on 2010-05-06
Gràcies per la informació. Ho tindré en compte per a la propera vegada.

Lluís

---

