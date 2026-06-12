---
title: "L'ordinador no em detecta els lectors de targetes."
date: 2009-03-13
forum: Catalan Team
---

### Post by oriolsbd on 2009-03-13
Tinc un Acer Aspire One, amb dos lectors de targetes. Avui acabo de veure que tinc el següent problema. Si arranco l'ordinador i hi poso una targeta (SD, per exemple) no me la reconeix. En canvi, si arranco l'ordinador amb la targeta ja posada, sí que me la reconeix. Això passa a tots dos lectors de targetes.

He provat de fer un "lspci" quan arrenco sense la targeta posada i un altre quan arrenco amb la targeta i veig que, efectivament, en el primer cas no em detecta el perifèric i en l'altre sí. Això ho veig perquè en el segon cas hi surten aquestes quatre línies:
```
01:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
01:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
01:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
01:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

També he fet un "dmesg" en ambdós casos. Veig que en un cas troba el dispositiu i en l'altre no, però no hi sé trobar el motiu. Em podríeu ajudar? Us passo els dos fitxers dmesg (dmesg_sense.txt.gz per quan no em detecta els dispositius i dmesg_ambdos.txt.gz per quan sí me'ls detecta).

Per cert, he provat totes les combinacions possibles de tenir en l'arrancada només una targeta, les dues o cap, però el resultat és sempre el mateix: només em detecta el dispositiu on hi ha la targeta des de l'arranc.

Gràcies.

---

### Post by papapep on 2009-03-13
Fa uns mesos, amb Debian però igual et funciona amb Ubuntu, ho vaig resoldre tal i com diu aquí:

[http://extralinux.net/?q=node/119](http://extralinux.net/?q=node/119)

amb el lector de l'esquerra, el de la dreta no l'he fet servir mai. Ni tan sols sé si funciona :)

---

### Post by oriolsbd on 2009-03-14
Hola, Papapep.

No m'ha funcionat. Al final, he trobat [aquesta anotació]("http://www.taringa.net/posts/linux/2277891/Instalar-Ubuntu-8_10-en-Acer-Aspire-One.html") on explica què cal fer. En resum, primer cal baixar-se aquesta shell i deixar-la al directori correcte:
```

wget http://petaramesh.org/public/arc/projects/AcerOne_Ubuntu/jmb38x_d3e.sh
sudo chmod 754 jmb38x_d3e.sh
sudo mv jmb38x_d3e.sh /usr/local/sbin/
```

S'ha d'editar:
```
sudo gedit /usr/local/sbin/jmb38x_d3e.sh
```
I canviar la línia 11, on posa:
```
modprobe pciehp
```
per:
```
modprobe pciehp pciehp_force=1
```
Per últim, s'ha d'editar el següent fitxer:
```
sudo gedit /etc/rc.local
```

I afegir aquesta línia abans de l'"exit 0":
```
/usr/local/sbin/jmb38x_d3e.sh
```

Moltes gràcies de tota manera. :-)

---

### Post by CarlesOriol on 2009-03-15
Gràcies per la solucio' oriolsbd a mi també m'anirà bé.

---

### Post by oriolsbd on 2009-04-30
Hola de nou.

Per tots els que, com jo, tingueu un Acer AspireOne, quan actualitzeu a Jaunty (si no ho heu fet ja) us trobareu amb el mateix problema que les SD només les detecta si ja les teníeu connectades abans d'engegar l'ordinador. Ja us havia passat aquestes instruccions per a arreglar-ho, però resulta que per a Jaunty s'ha d'arreglar d'una forma diferent (encara que molt més senzilla). El motiu pel qual ha canviat la forma d'arreglar-se és que el mòdul pciehp ja no es carrega amb "modprobe", sinó que ja ve precarregat en el mateix Kernel. Realment, per arreglar-ho és molt més senzill que amb Intrepid. Només cal fer el següent:

Editeu el fitxer menu.lst del grub:
```
sudo gedit /boot/grub/menu.lst
```
Busqueu la línia on hi posa:
```
# defoptions=quiet splash
```
I modifiqueu-la perquè quedi així:
```
# defoptions=quiet splash pciehp.pciehp_force=1
```
Deseu el fitxer i actualitzeu el grub:
```
sudo update-grub
```
El proper cop que arranqueu l'ordinador, ja us detectarà automàticament la targeta SD. He trobat aquestes instruccions en [aquest enllaç ]("http://blog.dieresys.com.ar/2009/04/06/eee-701-fnf2-en-ubuntu-jaunty-904-beta/")(són per a EeePC, però també funcionen per a l'AspireOne). Us recomano que el mireu, perquè també hi posa com solucionar un error de la Wifi.

Salut!

---

