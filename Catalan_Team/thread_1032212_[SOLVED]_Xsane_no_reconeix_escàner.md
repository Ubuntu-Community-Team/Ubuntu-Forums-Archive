---
title: "[SOLVED] Xsane no reconeix escàner"
date: 2009-01-06
forum: Catalan Team
---

### Post by Daerun on 2009-01-06
Quan engego el scanner, m'apareix una finestra del xsane on puc seleccionr la hauppage (la targeta de televisió) o el escàner. Quan selecciono aquest últim, em surt unmissatge que diu:

*No s'ha pogut obrir el dispositiu 'snapscan:libusb:002:004' : argument invàlid*

i sencillament es tanca l'aplicació :confused:

Abans, fa ja uns mesos, el que feia era cridar un script que circulava per poder fer anar l'escàner amb el virtualbox, però a part d'això el xsane sempre m'havia funcionat normalment.

---

### Post by enricXIII on 2009-01-06
D'allonsis... de quin escàner estariem parlant?

---

### Post by papapep on 2009-01-06
Aqui: [http://forum.ubuntu-fr.org/viewtopic.php?id=184857](http://forum.ubuntu-fr.org/viewtopic.php?id=184857)

parlen d'un problema com el teu. Lamentablement, el meu nivell de françois no és massa galdós...

Per cert, tampoc dius quina versió d'ubuntu fas servir...:-)

I si, pel que dius, abans anava i ara no, o has canviat alguna cosa (instal·lar, desinstal·lar, etc...), o alguna cosa física, el port USB, l'scanner, s'ha espatllat.

---

### Post by SiscoGarcia on 2009-01-06
> **papapep said:**
> Lamentablement, el meu nivell de françois no és massa galdós...

El tema de l'idioma no hauria de ser un problema, ja que a [http://xixona.dlsi.ua.es/apertium/ca/](http://xixona.dlsi.ua.es/apertium/ca/) ho poden solucionar (triant el sentit francès>català) ;)

---

### Post by Daerun on 2009-01-06
Ostres, sí, sempre m'oblido d'aquests detallets :P

Faig servir Hardy, i l'escàner es un Benq S2W 3300U

En principi no és el port usb, perquè avui mateix he provat de tornar a fer-lo servir amb el finestres del virtualbox i m'ha funcionat.

---

### Post by SiscoGarcia on 2009-01-06
Has mirat el que diuen a [http://foros.ubuntu-cl.org/viewtopic.php?t=995](http://foros.ubuntu-cl.org/viewtopic.php?t=995) on també tenen el mateix problema?

EDITO: Pel que veig sí que ho has mirat, ja que també hi participes ;)

Una altra possibilitat és a [http://ubuntuforums.org/showthread.php?t=469756](http://ubuntuforums.org/showthread.php?t=469756)

---

### Post by Daerun on 2009-01-07
Ostres sí, és el mateix fil on vaig participar fa un temps, la veritat és que no ho recordaba :lol:



Bé, la solució m'ha funcionat, per començar es fa el següent, amb l'escàner conectat

```
lsusb -v|grep id
```

Ens sortirá part del contingunt de l'arxiu lsusb a on podrem mirar el codi del producte, en el meu cas:

```
idProduct          0x20b0 S2W 3300U/4300U
```

(per saber on mirar cal conèixer el model del nostre escàner, és clar)

aquest 0x20b0 és l'identificador dels drivers que em fan falta a mi; canvia segons el model que tinguem. Cal comprobar a quin fitxer de drivers correspòn aquesta id. Jo fa temps que ho vaig mirar, i en el meu cas corresponia a l'arxiu "u176v046.bin" ubicat al paquet de drivers "mirascanv403u10_bqa.zip". El problema és que ara mateix no sé a on es podria mirar les correspondències en cas de voler comprobar un altre model :???:

Ara ve la part que jo no tenia feta. Aquest arxiu u176v046.bin s'ha d'ubicar dintre la carpeta /usr/share/sane/snapscan. Si la carpeta snapscan no existeix, es crea:

```
sudo mkdir /usr/share/sane/snapscan
```

i després s'hi copia l'arxiu:

```
sudo cp u176v046.bin /usr/share/sane/snapscan/
```

Ara cal configurar l'arxiu "snapscan.conf"

```
sudo gedit /etc/sane.d/snapscan.conf
```

al principi de tot s'hi pot trobar la següent línia:

```
firmware /usr/share/sane/snapscan/your-firmwarefile.bin
```

es substitueix el "your-firmwarefile.bin" pel nom de l'arxiu que acabem de copair a la carpeta snapscan... i ja está.

---

### Post by RainCT on 2009-01-08
M'alegro que ho hagis pogut solucionar, i que ho expliquis tant bé per si algú altre es troba amb el mateix problema!

Però... I el [SOLVED]? :)

---

### Post by Daerun on 2009-01-10
Volia intentar buscar allò que deia de com mirar l'arxiu que fa falta per a cada model de Benq/Acer, però no ho he trobar :P Així que au, ja está solves... vull dir solved.

---

