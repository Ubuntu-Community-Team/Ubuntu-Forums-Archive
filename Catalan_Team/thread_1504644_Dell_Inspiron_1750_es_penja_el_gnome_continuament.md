---
title: "Dell Inspiron 1750 es penja el gnome continuament"
date: 2010-06-08
forum: Catalan Team
---

### Post by RicardKp on 2010-06-08
M'acabo de comprar un Dell Inspiron 1750 de 17,3 polzades intel dual core i 4 gb de ram. Quan arriba a casa corro a esborra-li el windows 7 i a instal·lar el Lucyd... doncs no hi ha manera, el gome se'm penja cada dos per tres; de vegades, quan tinc dos usuaris oberts, se'm tanca el gnome. Els programes se'm tanquen sols, i els plugins del flash em peten cada dos per tres. He reinstal·lat els plugins, el flash, els restricted-extras i no sé quantes coses més no sé quantes vegades, al final he decidit reformatejar-lo i fer una instal·lació neta, a partir del Cd que m'havien enviat els de Canonical(l'anterior instal·lació l'havia fet aprofitant la configuració del meu Ubuntu 9.10 de l'ordinador de sobretaula i traspassant-la al nou 10.04). Doncs amb la instal·lació neta passa exactament el mateix, No sé si aquest portàtil no suporta correctament l'Ubuntu... no ho entenc, els controladors privatius sembla que funcionen correctament, no entenc, res... algú li ha passat el mateix amb un Dell?
Després de 4 anys de LInux sense massa problemes, ara no em crec que hagi de tornar a windows, és que no m'ho puc creure!

Hola Papapep, com veus he fet tot el que m'has dit a l'altre fil:

ricard-laptop:~$ uname -a
Linux ricard-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Més dades: Se m'ha penjat amb els següents programes, Firefox, Chromium, Writer Ooo, Jdownloader, VLC i segurament algun més. Quan tinc dos usuaris oberts es tanca el gnome i em porta a la pantalla de tria d'usuaris, i quan hi sóc veig que l'usuari amb el qual treballava s'ha tancat i l'altra que estava obert encara ho està.
 Gràcies, per endavant, al Papapep i a tothom qui em pugui ajudar

---

### Post by papapep on 2010-06-08
uhh...malament:

> 01:00.0 VGA compatible controller: **ATI** Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

Has provat a executar la sessió en mode segur per veure què passa sense el controlador de l'ATI?

---

### Post by RicardKp on 2010-06-08
D'acord ho provo i et dic el què.

Gràcies.

Edito: Al cap de 10 minuts ja m'ha petat el flash i m'ha sortit el següent missatge al chromium
*The following plug-in has crashed: /usr/lib/flashplugin-installer/libflashplayer.so*
Aquest missatge em sortia en la primera instal·lació i en la segona també, ja m'ha sortit 40 vegades com a mínim i ara amb mode a prova d'errors també.

---

### Post by papapep on 2010-06-08
Bé, doncs ja tens una, com a mínim, de les fonts del problema. Quan et peta el flash, et fa allò de reiniciar-te el servidor X o només et fa tancar/bloqueja el navegador? perque serien coses diferents, en teoria.

---

### Post by kimet on 2010-06-08
De passada pots fer una ullada als logs de /var/log, dmesg, syslog, xorg.0.log...A veure si hi trobes algun error o warning.

Salut.

---

### Post by RicardKp on 2010-06-09
Hola, Papapep,
Quan em peta el flash, només em tanca/bloqueja l'ordinador.

Hola, kimet,
Sóc un simple usuari d'Ubuntu, si he adjuntat els 2 fitxers és perquè, en un altre fil, el Papapep em va dir que obrís aquest i que adjuntés els 2 fitxers, però si jo me'ls llegeixo no en trec gtran cosa, i per suposat cap conclusió que em serveixi per arreglar el meu problema.

Salut i gràcies, a tots dos.

---

### Post by PatrickVogeli on 2010-06-09
has provat si tambe et pasa amb el firefox?

---

### Post by RicardKp on 2010-06-09
Se m'ha penjat amb els següents programes, Firefox, Chromium, Writer Ooo, Jdownloader, VLC i segurament algun més que ja no recordo. Aquesta tarda amb el mode gràfic a prova d'errors m'ha tancat tres vegades el jdownloader.

Vagi bé!

---

### Post by kimet on 2010-06-09
Pots posar les següents comandes i ajuntar els resultats, a veure si hi veiem alguna cosa:

```
sudo cat /var/log/Xorg.0.log

```
```
sudo cat /var/log/messages | tail -n 50
```

```
sudo cat /var/log/dmesg
```

```
sudo cat /etc/X11/xorg.conf
```
 
Aquest últim per sabr si utilitzes el driver privatiu de la gràfica.

---

### Post by RicardKp on 2010-06-11
Bé, kimet,

Aquí tens els adjunts que m'has dit. Espero que et donin alguna pista i moltes gràcies.

Ricard

---

### Post by kimet on 2010-06-11
Jo ni hi veig cap error.
Només el xorg.conf una mica escàs.
  
 Podries provar:

```
sudo aticonfig --initial
```

I hauria de generar un xorg.conf mes complert. 
Pero tingues en compte, de que en cas de que no funcioni podries haver de revertir la situació des de la tty, sense servidor x.
 
 De totes maneres si dius que en mode segur també et passa no crec que sol.lucioni res.
 
No se si vas provar l'ordinador amb w7, però seria la forma de descartar un defecte de hardware.

Salut.

---

### Post by RicardKp on 2010-06-12
D'acord, fa dies que penso en la possibilitat de provar el maquinari amb el windows7 original, em fa molta mandra i ràbia, però suposo que és el que toca.

Moltes gràcies,
Ricard

---

### Post by RicardKp on 2010-06-12
Hola, de nou,

Després d'instal·lar el windows7 m'he adonat que havia instal·lat l'Ubuntu en versió de 32bits i que el  Dell aquest té arquitectura de 64bits, pot ser aquest el problema? Pequè el windows no es penja gens i el chrome no té cap problema amb els connectors de flash.

Gràcies,
Ricard

---

### Post by kimet on 2010-06-12
No hauria de ser problema de la arquitectura, encara que tindràs millor rendiment amb la versió de 64bit.

Al meu parer tindries que intentar aïllar el problema, tot apunta a la targeta gràfica, pot ser provant els diferents drivers lliures, amb o sense KMS, diferents configuracions del xorg.conf, etc.
( A mi les ATI m'ha donat bon rendiment amb els drivers lliures)
 
Per saber si es el flashplayer el que et falla ho tens molt fàcil, el desinstal.les. (per cert no se si hi ha suport per a 64bits per part d'adobe)
 
També pots monitoritzar les temperatures i els processos a veure si n'hi ha algun que es queda travat.

---

