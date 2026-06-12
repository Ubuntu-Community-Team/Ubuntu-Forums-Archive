---
title: "Inici sessio lent Lucid"
date: 2010-04-30
forum: Catalan Team
---

### Post by kioni on 2010-04-30
Bona tarda a tothom, ahir a la nit vaig instal·lar el Lucid en partició nova nova (sense actualitzar anterior 10.09).
Una de cada 5 vegades que inicio el portàtil després de fer el redoble de tambo on apareixen els usuaris per posar el password, tard molt a apareixe l'opció després del so un cop aparegut i posat el password intenta entra a l'entorn gnome del escriptori pero abans em surt una finestra on diu que el Power Manager te un problema i dona 3 opcions una és cancelar, l'altre bloquejar la pantalla i la ultima surti de totes maneres, agafant aquesta ultima s'inicia el Lucid normalment, que li passa ? Perquè ho fa de vegades si de vegades no ? :confused:

He intentat varies coses com per exemple deshabilitar del menu aplicacions inicials el dimoni d'energia o en el menu de gestor d'energia deshabilitar l'opció de que surti la icona de carrega de bateria etc, etc  ... però sembla que encara ho fa quan vol.:(

La veritat és que no se que fer, voleu que pengi una captura de pantalla quan apareix l'error o que us dongui mes informació per mirar de trobar-hi alguna solució ?

Moltes gràcies. :)

---

### Post by kioni on 2010-05-03
El tema podria tenir a veure que tinc la bateria del portatil treta de vegades ?

Si la poso últimament ja no te capacitat de carrega i igual ja no la detecta com si estigues posada perque no surt la icona de bateria carregant-se.

He adjuntat una foto del missatge que surt d'error.

Alguna manera de que evitar aquesta incidència ?

---

### Post by kioni on 2010-08-12
He canviat la bateria per una de nova i el problema persisteix :(

---

### Post by pserra on 2010-08-13
> **kioni said:**
> He canviat la bateria per una de nova i el problema persisteix :(
Jo en el meu portatil no li he posat mai la bateria... ja que de seguida s'esgota amb la pantalla de 17''.. com que sempre estic endollat...

a mi em passava una cosa semblant...entre d'altres errors(wifi)..... fins que vaig reinstal·lar la lucid, i se'm va arreglar i l'engegada la tinc entre 40-45 segons... molt semblant al guindos 7...
quan et triga?

---

### Post by kioni on 2010-10-04
En ocasions uns 3 minuts i despres el sistema va lent

---

### Post by kimet on 2010-10-04
Quin portatil es i Quina BIOS té?.

Pots provar de canviar a la bios la opció SATA controller mode de AHCI a Compatibility. A mí em va funcionar en un toshiba amb la infame bios phoenix.

Salut

---

### Post by Black_02 on 2010-10-05
Hola,
A mi em passava el mateix, i jo no tinc un portàtil. L'únic que vaig fer va ser parar completament l'ordinador durant una bona estona (una nit).

Aquest problema és una mica estrany, perquè si el parava i després l'encenia el problema continuava sent-hi, inclús si iniciava un live cd. Es com si quedes un residu en la catxe (o on sigui, no en tinc ni idea) que no es borra fins al cap d'unes hores d'estar aparat.

El que hauries de fer és, una vegada dins l'ubuntu parar-lo completament, no temporalment ni hivernar (que és el que fa quan baixes la pantalla) i deixar-lo unes hores o millor una nit parat i si pots lleva-li la bateria i desendolla'l.

---

### Post by pserra on 2010-10-05
> **Black_02 said:**
> Hola,
A mi em passava el mateix, i jo no tinc un portàtil. L'únic que vaig fer va ser parar completament l'ordinador durant una bona estona (una nit).

Aquest problema és una mica estrany, perquè si el parava i després l'encenia el problema continuava sent-hi, inclús si iniciava un live cd. Es com si quedes un residu en la catxe (o on sigui, no en tinc ni idea) que no es borra fins al cap d'unes hores d'estar aparat.

El que hauries de fer és, una vegada dins l'ubuntu parar-lo completament, no temporalment ni hivernar (que és el que fa quan baixes la pantalla) i deixar-lo unes hores o millor una nit parat i si pots lleva-li la bateria i desendolla'l.

Jo la veritat, trobo que això de deixar el portàtil parat moltes hores perquè engegui més ràpid, un error, no sé que pensen els companys... però hi deu haver algun error a l'intal·lació/configuració

---

### Post by wgarcia on 2010-10-06
Hi ha a vegades càrregues d'electricitat estàtica que poden afectar algun funcionament, i possiblement deixant el portàtil unes quantes hores sense funcionar descarreguin aquesta electricitat estàtica, tot i que no és segur. El més probable és que hi hagi alguna cosa desconfigurada.

---

### Post by kioni on 2010-10-23
> **kimet said:**
> Quin portatil es i Quina BIOS té?.

Pots provar de canviar a la bios la opció SATA controller mode de AHCI a Compatibility. A mí em va funcionar en un toshiba amb la infame bios phoenix.

Salut
El portail es un Acer 5600, la Bios es una Phoneix versio 0.3128

Ara mateix com que veia que anava tan lent la versio 04.10, he reculat fins la versio Jahunty 04.09 que em funciona mes be, (pero clar, voldria posar la 04.10 perque es una LTS), una de les coses que vaig veure que era diferent es al carregar el sistema posava ACPI=off, en canvi en aquesta versio mes antiga posa ACPI - captable machine, no se si aixo es un indicador de on pot venir el problema ...

Respecte a posar a la bios la opció SATA controller mode de AHCI a Compatibility, ho he estat mirant i no se pas com es fa ... :(

En fi seguire investigant, gracies per les vostres respostes :)

---

