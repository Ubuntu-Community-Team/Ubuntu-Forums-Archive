---
title: "Problema a l'apagar Ubuntu 11.04"
date: 2011-05-08
forum: Catalan Team
---

### Post by elbogi on 2011-05-08
M'he instal.lat l'Ubuntu 11.04 al netbook Sony Vaio, però quan el vull apagar es queda penjat. Algú em pot dir com solucionar-ho? Per cert, sóc nou amb el tema Ubuntu i no controlo massa agrairia si fos possibles una resposta fàcil de saber dur a terme. Moltes gràcies.

elbogi :O)

---

### Post by wgarcia on 2011-05-11
Et surt algun missatge quan es queda penjat, o sols queda amb una pantalla gràfica sense cap missatge?

---

### Post by elbogi on 2011-05-12
No surt cap missatge. Només queda el color del fons de pantalla i no s'apaga. Només aconsegueixo apagar-lo fent-li una apagada forçada amb el botó. He llegit que també passava amb el 10.10, però no sé com solucionar-ho. Gràcies per endavant.

elbogi :O)

---

### Post by elbogi on 2011-05-12
Ja ho he pogut solucionar. No sé si han estat les actualitzacions que s'han baixat o bé el fet de fer el que posa en aquesta adreça.

[http://www.ubufaq.com/question/agp1YnVudHUtZmFxchALEghQcmVndW50YRjRgAUM](http://www.ubufaq.com/question/agp1YnVudHUtZmFxchALEghQcmVndW50YRjRgAUM)

se soluciona de esta manera:

abres una terminal y escribes lo siguiente:

sudo gedit /etc/modprobe.d/blacklist.conf

al hacer esto se abre un archivo

luego pones lo siguiente al final del archivo puedes copiar esas lineas y pegaralas tal y como estan:

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

cierras y salvas y apaga el equipo presionando el boton de encendido por ultima vez... ya que aun no esta funcionando lo que hiciste
despues enciendes y empezara a funcionar los cambios que hiciste
ya despues se debe apagar normal...

Espero que us pugui fer servei a qui li calgui i moltes gràcies per tot.

elbogi :O)

---

