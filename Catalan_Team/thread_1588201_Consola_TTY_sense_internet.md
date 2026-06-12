---
title: "Consola TTY sense internet"
date: 2010-10-04
forum: Catalan Team
---

### Post by catbru on 2010-10-04
Hola!
Avui m'he posat a remanar els controladors de la tergeta gràfica intel del portàtil per millorar el seu rendiment i resulta que desinstalant un controlador que no m'anva bé m'he quedat sense entorn gràfic.
Ara, quan encenc l'ordinador, arriba bé fins a la pantalla de càrrega d'Ubuntu, aquesta dels puntets que es van il·luminant, però aquí es queda. El cas és que estic pràcticament segur que es podria resoldre amb un simple apt-get update o similar (per com ha anat) però em trobo amb un problema.
Quan encenc l'ordinador, després de la pantalla per accedir a la BIOS no em surt cap referència al GRUB, només un guió pampalluguejant tipus consola durant uns qutre segons. Durant aquest temps he prova d'apretar shift, esc, maj., i tot el que m'ha passat pel cap però no hi ha manera d'accedir al menú de GRUB, que em permetria entrar com a recovery mode.
Així, deixo passar el guionet i quan sóc a la pantalla d'ubuntu faig alt+f1 i efectivament entro a la consola TTY, faig login, però sorpresa, em trobo que no té conexió a internet (i altres coses estranyes, com que em diu que gedit no està instal·lat).
Tinc diverses preguntes, és possible que no tingui el GRUB instal·lat? Si és així com entro com a recovery mode?
És normal que la consola TTY no tingui internet? Com que el problema és de la targeta gràfica, hauria de mantenir la conexió automàtica a internet, oi?

I per curiositat, quina diferència hi ha entre la consola 'normal' i la TTY?

Moltes gràcies!

---

### Post by kukat on 2010-10-04
Has provat de fer-ho des del CD-ROM???

amb un 
**sudo dpkg-reconfigure xserver-xorg **

??

I a "/usr/local/sbin/" no està "gedit" ???
o /sbin/gedit ??? 

(açò últim no estic segur)

---

### Post by kukat on 2010-10-04
Has provat de fer-ho des del CD-ROM???

amb un 
**sudo dpkg-reconfigure xserver-xorg **

??

I a "/usr/local/sbin/" no està "gedit" ???
o /sbin/gedit ??? 

(açò últim no estic segur)

---

### Post by kimet on 2010-10-04
Network-manager depèn del entorn gràfic i gedit també.
Cal que utilitzis altres editors (nano, vim..) i altres gestors de xarxa (wicd).

Salut.

---

### Post by kukat on 2010-10-04
ostres clar!
oblida el de ***/usr/sbin*** i el de ***/sbin***....
únicament hi ha programes com el "iptables" que no depèn de l'entorn gràfic!

lamente la confusió, però estava fent unes coses al Guindow$ i no ho podia comprovar....
;)

---

