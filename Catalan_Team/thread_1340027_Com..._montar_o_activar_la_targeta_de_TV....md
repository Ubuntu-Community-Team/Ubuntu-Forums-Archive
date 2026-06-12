---
title: "Com... montar? o activar la targeta de TV..."
date: 2009-11-28
forum: Catalan Team
---

### Post by Black_02 on 2009-11-28
Hola,
Tinc l'ubuntu 9.10 i una targeta TDT la pinnacle 310i (Philips TDA10046H DVB-T), el problema és que l'ubuntu la detecta bé però no sintonitza els canals de TV, però quan arrenco el Windows i la faig funcionar, si reinicio** sense parar l'ordenador**, tan sols reiniciant i arrancant l'ubuntu, aleshores em funciona perfectament, en canvi si paro l'ordenador i després l'encenc directament amb l'ubuntu ja no em funciona:confused:.

Es com si el Windows actives la targeta i al reiniciar amb l'ubuntu sense parar la maquina, aquest la detectes correctament.

La veritat és que és un rollo haver de iniciar Windows abans de Ubuntu per poder veure la tele[-(.

---

### Post by rroca1 on 2009-11-29
Em sembla estrany. Jo el que vaig fer va ser:

Anar a Sistema / administració /controladors de maquinari, l'ubuntu la va trobar, va descarregar drivers  i la faig funcionar amb MeTv. Amb Kaffeine no em funciona al portàtil però si al de sobretaula  (el primer té gràfica intel integrada i el segon NVIDIA)

Cal assegurar-se que tens tot el que li fa falta per a funcionar. 

Espero que et serveixi

---

### Post by Black_02 on 2009-11-29
Hola rroca1,
He mirat que em dius, però tan sols em surt la targeta gràfica (ATI/AMD), però problema no són el drivers, ja que la targeta TDT la detecta, el problema és com si no estes habilitada (crec que és algo paregut als disc dur, que l'has de motar).

De fet ara estic mirant la tele des de Ubuntu, però perquè abans havia iniciat el Windows.

Se que sembla molt estrany, però es el que hi ha :???:. Estic segur que la solució és senzilla però ha saber quina és :confused:.

---

### Post by guillemsola on 2009-11-29
Hola,

normalment les tarjetes de video en linux en funcionar per primera vegada han de carregar un firmware a la tarjeta per funcionar correctament.

Aquests firmwares són propietaris i no es poden distribuir amb linux, ara bé si els tens des de windows els pots copiar a /usr/bin/firmware (crec) i aleshores quant el linux els vulgui carregar els trobara.

Hauríes d'adjuntar el dmesg de quant després de voler sintonitzar amb la tarjeta per veure si diu que intenta pujar tal firmware i que no el troba.

Si passes per [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page) segurament trobaras més info.

---

### Post by Black_02 on 2009-11-30
Angrychai, ets un crack!! =D>

No ho hagués dit mai que fos una solució de copy & paste.

Moltes gràcies :grin:.

---

