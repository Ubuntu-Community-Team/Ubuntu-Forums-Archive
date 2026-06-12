---
title: "No puc accedir al meu usuari després d'actualitzar a Ubuntu 10.10"
date: 2011-01-04
forum: Catalan Team
---

### Post by ximoberna on 2011-01-04
He fet una actualització del sistema de Ubuntu 10.04 a Ubuntu 10.10 aprofitant una partició prèvia /home i matxacant només la partició de sistema / 

En el procés d'instal·lació he posat un nom de superusuari igual al que hi havia i el problema és que ara no puc accedir a aquest, ni a cap altre, perquè no puc ni tan sols crear un nou usuari... No puc llançar una consola des de la pantalla de logueig inicial que és a on puc arribar després d'apareixer grub..

Per a intentar explicar-me una cosa que no m'havia passat mai des de que soc usuari de linux, i ja fa alguns anys d'això fent actualitzacions de sistemas sobre /..., crec que, a no ser que m'haja oblidat de la contrasenya de root mentrestant :-P, és que les dades de l'usuari estan encriptades (em pense que ho vaig fer en instal·lar la 10.04) i ara aquesta actualització no reconeix les dades del superusuari, però, per què no puc accedir via consola???

Si em podeu ajudar vos ho agrairia.

Salutacions i bon any a tota la comunitat

---

### Post by kimet on 2011-01-04
No acabo d'entendre exactament el que et passa, de totes maneres sempre pots crear un nou usuari des de un live cd.
Muntes el disc i amb ```
chroot /punt/de_muntatge
```
Estarás com root en la partició, des de aqui fas el ```
adduser xxx
```
Tambe pots crear una partició home i modificar /etc/fstab perque la usi en contes de la que tens xifrada.

Salut

---

### Post by ximoberna on 2011-01-05
Sembla que el problema era accedir al perfil xifrat... 
Estic accedint des d'un nou usuari.
Però, això que dius em sembla que no hi ha solució per al contingut xifrat a /home???

Tanmateix he fet còpia de seguritat abans de tot això :-P

Salutacions i moltíssimes gràcies per contestar en mig de la dèria de les compres de Reis!

---

### Post by kimet on 2011-01-05
No hi ha res que no tingui sol.lució.

Es probable que el sistema nou no sàpiga que la partició home està xifrada, s'hagin perdut els links... No s'hagin carregat els mòduls...

 Hauries de saber quin programa vas fer servir per xifrar la partició i consultar la documentació. (moduls que utilitza, fitxers de configuració)
Es possible que quedés algun backup??

Salut.

---

### Post by ximoberna on 2011-01-05
Vaig usar l'opció de xifratge del mateix Ubuntu en instal·lar-lo l'any passat. No sé quin programa és exactament però si teniu alguna idea... He intentat entrar en el dit usuari com a usuari normal creat per això i m'han aparegut missatges d'error, a banda de no carregar-se gràficament el dit perfil. Després comentaré els missatges...

---

### Post by wgarcia on 2011-01-06
Mira si les instruccions d'aquest blog et serveixen, clar que suposen que recordes la clau de xifratge del "home":

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by ximoberna on 2011-01-07
Vet aquí que no em vaig preocupar de saber aquesta clau de xifratge...

Els missatges d'error als quals al·ludia abans són:

El Nautilus no ha pogut crear les carpetes /home/usuari/Desktop...

Hi ha un problema amb el servidor de la configuració /usr/lib/libconf2-4/gconf-sanity-check-2 ha sortit amb l'estat 256

Couldn't update ICEauthoriy file /home/usuari/.ICEauthority


Gràcies tanmateix!

---

### Post by wgarcia on 2011-01-07
Em sembla que això és un problema de permisos d'aquest fitxer ".ICEauthority" i possiblement també del teu usuari. 

Fes des d'una terminal:

cd /home

ls -l

i et mostrarà el propietari i permisos del teu home. Si no fossin correctes pots arreglar-ho amb

sudo chown usuari:usuari /home/usuari

El fitxer .ICEauthority el pots eliminar i el sistema el recrearà en reiniciar si continua donant problemes.

---

