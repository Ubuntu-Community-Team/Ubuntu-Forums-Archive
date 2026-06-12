---
title: "Rhythmbox i Ubuntu 9.10"
date: 2010-02-09
forum: Catalan Team
---

### Post by jdk9 on 2010-02-09
Bones de nou!

Bé, després de la pausa obligada per examens, torno a demanar coses xD... Ara, quan escolto musica amb el Rhythmbox, al cap d'una estona, i just quan acaba una cançó, el reproductor es tanca per si sol. 

Uso Ubuntu 9.10 de 64 bits, i tot i googlejar, el que he trobat no m'ha funcionat.

Apa salut!

---

### Post by oriolsbd on 2010-02-09
Executa el Rhythmbox des d'un terminal per mitjà de la comanda:
```
rhythmbox %U
```

Escolta música amb el Rhythmbox. Just quan se't tanqui sol, seguramente et deixarà algun missatge d'error en el terminal des del que l'hagis executat. Envia'ns aquest missatge que et deixi.

Salut!

---

### Post by idrox on 2010-02-10
Jo l'utilitzo sovint (en el de 32, no en el de 64) i mai m'ha donat aquest problema... sols que de tant en tant l'obro, i quan poso per reproduir no es reprodueix (és a dir, es selecciona la cançó i tal, però no passa del segon zero). Quan em passa això, reinicio el programa i ja està.


Però l'error que dius tu... no m'ha passat (i espero que no em passi) mai!

---

### Post by jdk9 on 2010-02-10
Bé, he fet rhythmbox %U i no m'ha retornat res; després he fet rhythmbox i m'ha retornat Segmentation fault ... no sé que vol dir am aixó :S

He buscat una mica i aixó només passa a la versió de 64 bits, i és un bug que ja ha estat reportat: 
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624)
i ho estic provant amb el gconf-editor i no funciona, la casella està marcada.

Gràcies per les respostes!

---

### Post by jdk9 on 2010-02-11
Bé problema solucionat: Banshee , el Rhythmbox cada cop anava pitjor (ara ja ni acabava les cançons :S)

Gràcies per les respostes!

---

### Post by CarlesOriol on 2010-02-13
Doncs no veig que sigui el mateix bug que comentes: 

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/192624)
rhythmbox **doesnt start** and shows the error "Segmentation fault" in terminal.
System: **Ubuntu 8.04** AMD64 with upgrades

---

### Post by jdk9 on 2010-02-14
Ja ho vaig veure que era per el 8.04 però vaig suposar que al ser també la versió de 64 bits i que estava actualitzada, aleshores podria ser la mateixa sol·lució.

Gracies de nou per les respostes!

---

