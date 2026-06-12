---
title: "Actualitzar Ubuntu"
date: 2007-03-09
forum: Catalan Team
---

### Post by nachocan on 2007-03-09
Hola a tots,

Es el meu segon post, demanant ajuda (de principiant), i encaa no he pogut ajudar a ningú, perquè la veritat entre el foro i la llista, hi ha un nivell que a vegades m'espanta i tot, però bé anirem aprenent...

Vull saber quin es el procés correcte per actualitzar l'Ubuntu a la nova versió. M'explicaré he estat llegint que a l'Abril surt la versió 7 de l'Ubuntu, i com és normal, la voldré probar, ja que segur que és millor que la 6.10 que ara faig servir (i la primera). 

Estic interessat en saber com estalviar-me feina, ja que tinc l'evolution funcionant y el faig servir de programa de correu, contactes, organitzador, notes,... sobre aquest tema ja he trobat unes línies de codi per a generar un arxiu comprimit amb totes les dades impòrtants de l'evolution, per poder-les migrar de pc. 

Pero el que vull saber es si hi ha alguna marera de guardar les aplicacions que tinc instalades, de manera que a l'actualitzar el nou Ubuntu, ho executi d'alguna manera i m'instali els paquets que faig servir habitualment, ja que suposo que copiar tot el que hi ha al meu directori personal no serà una bona opció??

Gràcies a tots.

---

### Post by CarlesOriol on 2007-03-09
Si .... per que no?... migrant el /home/elteunom tindràs més de la mitat de la feina feta.

Pots fer això per sincronitzar a un disc usb si vols:

	rsync -urvt --delete  /home/elteunom /media/usbdisk/copies

i despres restaures amb un:

          rsync -rtv /media/usbdisk/copies/elteunom /home

Si vols fer una copia de la llista de paquets instal·lats pots fer-ho amb:
 
           dpkg --get-selections > elsmeuspaquets.txt

... al restaurar-ho pots usar el "simpàtic" (synaptic) però vigila d'eliminar els paquets dependents de versió o de maquinari (si canvies d'ordinador)... linux-image , pograma-vX.XX

             segur que et sorprendràs quan vegis com n'és de fàcil!!

---

### Post by CarlesOriol on 2007-03-09
M'oblidava...

Malgrat que el sistema de fer copies que t'he comentat va força bé. En les proves del Herd5  el procés de migració d'usuaris és gairebé perfecte fins i tot si tens una partició en una versió diferent i la vols conservar ell automàticament et transporta la informació dels usuaris.

---

### Post by nachocan on 2007-03-09
Moltes gràcies per l'ajuda CarlesOriol, ho he preguntat per dues raons:

-El meu portàtil té 27GB de disc dur i em funciona correctament, tant amb Ubuntu com amb Windows XP, per tant de moment no tinc cap necessitat de canviar-me'l, però el disc dur se'm queda just per tenir els dos sistemes operatius instalats, i l'Ubuntu veig que necessita més de les 10GB que li he assignat, ja que vaig afegint paquets i tot això i l'espai lliure es va reduïnt cada dia.:(  Per tant compraré un altre disc dur i vull migrar el sistema que ara tinc instal·lat.

-D'altra banda com que a l'abril sortirà l'Ubuntu 7, m'hi vull apuntar que segur que incorpora millores. 

Probaré tot el que m'has explicat i ja us comentaré si me n'he sortit o no. 

Seguim en contacte.

---

### Post by Naonak on 2007-03-10
Bones!

Quan tinguis la migració feta, per actualitzar la versió que tens a feisty el que has de fer és el següent:

1. Editar el sources.list. Obre un terminal (Aplicacionjs/Accesoris/Terminal):
```
sudo gedit  /etc/apt/sources.list
```

Substituir les entrades **edgy **per **feisty** i guardar.

2. Refrescar els repositoris:

```
sudo apt-get update
```

3: Aplicar les actualitzacions:

```
sudo apt-get dist-upgrade
```

No sé quin tamany tindrà la descàrrega, però seran centenars de megas, és a dir, paciència!

Et demanarà reiniciar i un cop fet ja tindràs l'ubuntu actualizat.

Salut!

---

### Post by CarlesOriol on 2007-03-10
Si tot va bé sols cal posar el cd nou i quan digui que troba una versió nova i ens pregunta si volem afegir-lo als origens del gestor de paquets li diem que si.

Em sembla que llavors ell et fa el dist-upgrade.

---

### Post by nachocan on 2007-03-13
CarlesOriol: Tenies tota la raó, amb les instruccions que m'has donat, he fet la restauració del sistema en un nou disc dur sense cap complicació (excepte el temps que he trigat en fer-ho). A partir d'ara faré servir la instrucció de copia de seguretat cada setmana. 
Només hem falta entendre aquest tipus d'instruccions per a poder aprendeles de memoria, ja que si no entenc la lògica poca cosa faré :) 

Naonak: Gràcies per la teva ajuda, però encara no ho he provat, ja que l'actualització del sistema la faré el proper mes, i crec que hem serà fàcil, ja que ara tinc el sistema en una partició, i el /home en una altra que no hauré de borrar. 

Gràcies a tots, ja comentaré com me'n surto amb l'actualització.

---

