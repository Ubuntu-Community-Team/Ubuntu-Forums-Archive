---
title: "ttf-mscorefonts-installer"
date: 2009-11-18
forum: Catalan Team
---

### Post by Daerun on 2009-11-18
He fet una instal·lació nova del Koala, i en voler instal·lar el Wine, s'hi incloia com a dependència el paquet del títol. També consta com a dependència de ara no recordo quin altre programa, crec que dins dels restricted-extras.
Bé, el cas es que la instal·lació d'aquest en concret es va quedar com penjada: primer va fallar; cap problema, sencillament el vaig ignorar i vaig tancar el synaptic; però després, al dia següent, en voler instal·lar una altra cosa, va torna a aparèixer: és a dir, que el Synaptic el va voler tornar a instal·lar, sortia com a marcat (em pensaba que els canvis només es mantenien dins de la mateixa sessió, però que si apagaves l'ordinador no es guardaven), però tornava a fallar.
Ahir el vaig marcar per desinstal·larlo, i avui he intentat de tornar a instal·lar-lo, i surt el següent missatge:

[I]El paquet ttf-mscorefonts-installer no té una versió disponible, però existeix a la base de dades.
Això normalment vol dir que el paquet estava mencionat en una dependència i mai es va apujar, és obsolet o no és disponible amb els continguts de sources.list[/I]

En principi, amb aquest paquet s'instal·len les fonts del finestres, que són necessàries per què determinats programes funcionin correctament amb el Wine, algú en sap res?

---

### Post by papapep on 2009-11-18
Prova a fer un:

```
sudo aptitude update && sudo aptitude install ttf-mscorefonts-installer
```

El paquet [hauria de ser-hi]("http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer").
Verifica també que tens el repositori "multiverse" activat.

Si et segueix fallant, prova a canviar de servidor de paquets, i torna a executar la ordre.

---

### Post by Daerun on 2009-11-18
Gràcies, he fet tot el que em dius, però segueix igual. Aquests són els missatges que apareixen mente s'intenta instal·lar.

```
--2009-11-18 17:26:43--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolent downloads.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «downloads.sourceforge.net»
--2009-11-18 17:26:53--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent switch.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «switch.dl.sourceforge.net»
--2009-11-18 17:27:03--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent mesh.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «mesh.dl.sourceforge.net»
--2009-11-18 17:27:13--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent dfn.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «dfn.dl.sourceforge.net»
--2009-11-18 17:27:23--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent heanet.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «heanet.dl.sourceforge.net»
--2009-11-18 17:27:33--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent jaist.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «jaist.dl.sourceforge.net»
--2009-11-18 17:27:43--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
S'està connectant a nchc.dl.sourceforge.net|211.79.60.17|:80... conectat.
HTTP: Petició enviada, esperant resposta... 302 Found
Localització: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net [el següent]
--2009-11-18 17:27:49--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolent downloads.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «downloads.sourceforge.net»
--2009-11-18 17:27:59--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent ufpr.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «ufpr.dl.sourceforge.net»
--2009-11-18 17:28:09--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent internode.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «internode.dl.sourceforge.net»
--2009-11-18 17:28:19--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent voxel.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «voxel.dl.sourceforge.net»
--2009-11-18 17:28:29--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent kent.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «kent.dl.sourceforge.net»
--2009-11-18 17:28:39--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolent internap.dl.sourceforge.net... Fallat: Connection timed out.
wget: no s'ha pogut resoldre l'adreça del servidor «internap.dl.sourceforge.net»
sha256sum: andale32.exe: No such file or directory
andale32.exe: no s’ha pogut obrir o llegir
sha256sum: avís: 1 de 1 fitxer llistat no s’ha pogut llegir
Checksum mismatch for andale32.exe, aborting!
dpkg: s'ha produït un error en processar ttf-mscorefonts-installer (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 ttf-mscorefonts-installer

```

El què entenc és que el paquet s'ha baixat, però després, per instal·lar-se, es connecta a algun lloc per descarregar les fonts, però no pot...

---

### Post by papapep on 2009-11-18
Això sembla, sí. Pots obrir una comunicació d'error al Launchpad per avisar del que passa, o esperar-te uns dies a veure si algú ho resol.

---

### Post by blas.lopez on 2009-11-26
Mira això:

[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

> **Daerun said:**
> He fet una instal·lació nova del Koala, i en voler instal·lar el Wine, s'hi incloia com a dependència el paquet del títol. També consta com a dependència de ara no recordo quin altre programa, crec que dins dels restricted-extras.
Bé, el cas es que la instal·lació d'aquest en concret es va quedar com penjada: primer va fallar; cap problema, sencillament el vaig ignorar i vaig tancar el synaptic; però després, al dia següent, en voler instal·lar una altra cosa, va torna a aparèixer: és a dir, que el Synaptic el va voler tornar a instal·lar, sortia com a marcat (em pensaba que els canvis només es mantenien dins de la mateixa sessió, però que si apagaves l'ordinador no es guardaven), però tornava a fallar.
Ahir el vaig marcar per desinstal·larlo, i avui he intentat de tornar a instal·lar-lo, i surt el següent missatge:

[I]El paquet ttf-mscorefonts-installer no té una versió disponible, però existeix a la base de dades.
Això normalment vol dir que el paquet estava mencionat en una dependència i mai es va apujar, és obsolet o no és disponible amb els continguts de sources.list[/I]

En principi, amb aquest paquet s'instal·len les fonts del finestres, que són necessàries per què determinats programes funcionin correctament amb el Wine, algú en sap res?

---

### Post by Daerun on 2009-11-26
Mmmmm, no funciona gaire bé això, em surt aquest missatge:

```
cp: ha fallat stat() sobre «andalemo.ttf»: No such file or directory
cp: ha fallat stat() sobre «ariblk.ttf»: No such file or directory
cp: ha fallat stat() sobre «impact.ttf»: No such file or directory
cp: ha fallat stat() sobre «webdings.ttf»: No such file or directory

```

Suposo que les altres que no donen error sí s'hauran instal·lat...

---

