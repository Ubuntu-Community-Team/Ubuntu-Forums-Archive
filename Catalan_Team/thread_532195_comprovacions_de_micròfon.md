---
title: "comprovacions de micròfon"
date: 2007-08-22
forum: Catalan Team
---

### Post by xoldy on 2007-08-22
Hola a tots, no se per quina rao fa uns dies em funcionava el micròfon i avui he intentat fer una videoconferència amb l'amsn i no em funcionava.

Hi ha alguna comprovació que pugui fer per veure que està fallant?
He anat a l'enregistrador de so i no m'ha funcionat.
Tinc un portàtil HP nc8430, i el so no em falla. Sembla que només afecta el micròfon.

Em podeu encendre la bombeta?
Moltes gràcies

---

### Post by papapep on 2007-08-22
Per començar podries anar a mirar al mesclador de Gnome que no tinguis  el microfon "mutejat" ni el volum de captura baix. Ja sé que abans et funcionava, però a vegades a passat això sense cap raó aparent.

Si no hi veus res extrany, també seria bó fer un cop d'ull al mesclador d'alsa en consola, que té més controls i fer la mateixa verificació. A mi em va passar un cop ;-)

---

### Post by xoldy on 2007-08-22
Aparentment tot està correcte, tots els volums a tope. i sense el mute posat en el micròfon. No se com he de fer entrar i configurar per consola. Em pots orientar si us plau?
Moltes gràcies

---

### Post by papapep on 2007-08-22
Ostres, ara no tinc el portàtil a mà...crec que es deia "alsamixer" tal qual...

O sigui, que executis el programa "alsamixer" en un terminal.

---

### Post by xoldy on 2007-08-22
Moltes gràcies papapep, era aquesta la comanda. t'envio una captura de pantalla del que surt. aparentment tot a dalt, però el mic em fa sospitar que alguna cosa no funciona.
Que més puc mirar?

---

### Post by papapep on 2007-08-22
La tercera posició "mic capture" la tens avall de tot i en vermell. Fica-t'hi a sobre amb les fletxes esquerra i dreta i un cop a sobre no recordo si era amb la barra espaiadora o amb l'intro que s'activava. Per cert, si fas fletxa a la dreta veuràs que tens més controls que els que veus amb la captura que m'has enviat (si no ho has vist ja).

---

### Post by papapep on 2007-08-22
Per si no et funciona el que t'he dit, aquí tens uns quants enllaços que parlen del tema (n'hi ha molts més):

[http://www.ubuntu-es.org/index.php?q=node/57431](http://www.ubuntu-es.org/index.php?q=node/57431)
[http://www.ubuntu-es.org/index.php?q=node/41560](http://www.ubuntu-es.org/index.php?q=node/41560)
[http://www.ubuntu-es.org/index.php?q=node/14759](http://www.ubuntu-es.org/index.php?q=node/14759)

---

### Post by xoldy on 2007-08-22
Hola papapep, en teoria per activar i desactivar el control és amb la m, M. De tota manera no em funciona. Podria tenir a veure amb algun problema de hardware? Puc "reinstal·lar" el so?

Moltes gràcies

---

### Post by papapep on 2007-08-22
> Podria tenir a veure amb algun problema de hardware?

Home, si et refereixes a si pots tenir una avaria, doncs sempre és possible. Respecte incompatibilitats, no hauria de ser donat que has esmentat que t'havia funcionat abans. També podria ser que hagis instal·lat o desinstal·lat algun paquet que t'hagi malmés la configuració del só.

> Puc "reinstal·lar" el so?

Amb Linux, tot és possible ;-) (o gairebé...)

Però abans potser seria bó que fessis un cop d'ull als enllaços que t'he passat abans. 

Si segueixes sense sol·lució:

```
sudo dpkg-reconfigure alsa-base alsa-utils gnome-alsamixer
```

(i així no els reinstal·laràs, sinó que provarem a veure si tornant a configurar-los s'arregla)

---

### Post by xoldy on 2007-08-22
hola papapep, he mirat els tres enllaços i a tots ells he pogut veure una mica el que he anat provant. de tota manera a la pestanya s'està enregistrant del alsamixer només em surten les barres de volum de "capture", malgrat que per edita+preferències tinc marcada l'opció microphone. adjunto imatges.

He provat la comanda pel terminal que m'has enviat i no ha fet res de nou.

Moltes gràcies

---

### Post by papapep on 2007-08-22
Doncs provem a reinstal·lar:

```
sudo apt-get install --reinstall alsa-base alsa-utils gnome-alsamixer
```

Si no et va hauràs de verificar que el maquinari et funciona bé, i, fins i tot, tornar a repassar l'alsamixer.

---

### Post by xoldy on 2007-08-22
Ara m'hi poso. Moltes gràcies

---

### Post by xoldy on 2007-08-22
No hi ha manera.
Soc en via morta. Em fa por provar més coses, perquè ara encara puc escoltar so.

No se penso que ho consultaré amb el coixí.

Bona nit

---

### Post by pespin on 2007-08-22
Has provat en un altre ordinador el micro, no sigui que s'hagi escarxofat el maquinari? mai se sap :)

Pot ser que tinguis a la pestanya de commutadors el LineIn o un d'aquests enves del micro i per això no vagi? 
A falta de saviesa bones són les idees espero jeje

---

### Post by xoldy on 2007-08-27
Hola pespin, segueixo sense que em funcioni. Ja he provat en una altra màquina i no és problema del micròfon.

Estic per reinstal·lar tot l'Ubuntu.

Podria ser que s'arregli amb el canvi a Gutsi? Serà recomanable el canvi?

Moltes gràcies
Segueixo buscant jo també

---

### Post by pespin on 2007-08-27
Pel que sé el Gutsy encara està en versió beta, o sigui k tu veuràs el que fas si te'l poses8-[

Per altra banda si tens instal·lat algun altre SO en el mateix ordinador podries provar, així també traiem la possibilitat de ser problema de la tarja de so.
Has provat de posar-li el micro boost aquest que tenen? jo he tingut problemes alguns cops per això.

---

### Post by xoldy on 2007-08-27
Hola bona tarda, encara no vull posar la Gutsy fins que no sigui oficial.

El tema Mic Boost l'he provat i no hi ha manera. Penso que farè paciència, i ho deixo per més endavant. a veure si actualitzant torna a funcionar.

Moltes gràcies a tots pel vostre temps

---

