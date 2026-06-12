---
title: "[SOLVED] SOS he perdut el grub"
date: 2007-10-09
forum: Catalan Team
---

### Post by siscuboontu on 2007-10-09
Hola, hola,

Hi ha algú que pugui dir-me com reinstal·lar (?) el grub? Acabo de perdre la possibilitat d'arrencar l'ordinador on tinc la Gutsy i ara començo aquest fil des del finestres.

El que m'ha passat és que he volgut treure del grub les edicions velles del kernel i quedar-me només amb la nova editant el menu.lst; després de fer-ho, per comprovar si me n'havia sortit, he fet "reboot" a la consola i ha començat a pitar com un boig i ja no ha arrencat. Només surt grub>  amb una pantalla negra de fons i no em deixa fer res. Diu:

[INDENT]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.

grub>
[/INDENT]

Llavors si pitjo el tabulador em surten les diverses possibilitats que tinc: 

Possible commands are: background blocklist boot border cat chainloader clear cmp color configfile debug displayapm embed find foreground fstest geometry halt help impsprobe initrd install ioprobe kernel lock makeactive map md5cryot module modulenounzip pager partnew parttype password pause print quiet read reboot root rootnoverify savedefault serial setkey setup shade splashimage terminal terminfo testload testvbe unhide uppermem vbeprobe viewport


Què puc fer???????:confused:

---

### Post by CarlesOriol on 2007-10-09
1. Engega amb la live
2. sudo grub
3. root (hd0,2)
(2 o el nombre de la partició on guardarem el menu.lst
4. setup (hd0)
5. quit

i renicies... fàcil no?

---

### Post by siscuboontu on 2007-10-09
Gràcies Carles per respondre tan aviat, però o no faig el que dius o hi ha un altre problema; això si és que jo t'ho he explicat bé.

Veuràs, el que he fet és obrir la consola i en escriure el que dius (provant totes les possibilitats) em diu que no pot muntar la partició seleccionada (hd0, entenc jo). Potser el problema és que enlloc d'això li hauria de dir que muntés la que té la swap?

Adjunto una captura que he fet amb el disc partit com el veu el GParted.

Gràcies.

---

### Post by siscuboontu on 2007-10-09
Hola un altre cop (i definitiu per aquest fil),

Tenies raó (m'atreviria a dir que com sempre) i he repetit el procés, fins que me n'he adonat que no havia provat la partició 2, on hi havia el menu.lst

Ho he fet seguint les teues instruccions i me n'he sortit.

Milers de gràcies,

Sisco:guitar:

---

