---
title: "[RESOLT] formatar disquet - Dues preguntes:"
date: 2007-05-29
forum: Catalan Team
---

### Post by prostata on 2007-05-29
És tracte del seguent:

A) Quin programa hi ha als repositoris per formatejar un diskete de 1.4, els de sempre, es pot integrar dins mateix del Nautilus?

B) He posat un disket del mateix model de (A) i al Nautilus i surt, Disquet 1| Disquetera, en cap cas puc accedir al disket inserit, em dona com a reposta el seguent: " no es pot montar el volum" detalls: mount: you must specify the file type". mount/dev/is not a block device.

¿com puc fer per veure el disket al nautilis i poder tractar amb ell de forma natural???

moltes gràcis

---

### Post by crazyserver on 2007-05-29
**Resposta a  A:**
*gfloppy* em sembla que es diu, serveix per formatar disquets però que jo sapiga no s'integra amb el *Nautilus*. De fet diria que el *gfloppy* ve instal·lat per defecte amb ubuntu i el trobaràs a eines del sistema, si no... per linia de comandes ;)
[B]
Resposta  a B:[/B]
Assegura't de que a /etc/fstab tinguins una linia semblant a aquesta:
*/dev/fd0        /media/floppy   auto            rw,user,noauto                          0       0*

---

### Post by prostata on 2007-05-29
> **crazyserver said:**
> **Resposta a  A:**
*gfloppy* em sembla que es diu, serveix per formatar disquets però que jo sapiga no s'integra amb el *Nautilus*. De fet diria que el *gfloppy* ve instal·lat per defecte amb ubuntu i el trobaràs a eines del sistema, si no... per linia de comandes ;)
[B]
Resposta  a B:[/B]
Assegura't de que a /etc/fstab tinguins una linia semblant a aquesta:
*/dev/fd0        /media/floppy   auto            rw,user,noauto                          0       0*

he vist el fstab i no hi és el que dius, però quan ho vull escriure em diu que no tinc permis, ¿com ho faig?? da'ltre costat el gfloppy no em funciona malgrat ternir-lo activat al synaptic...

---

### Post by crazyserver on 2007-05-29
Suposo que no et funciona el *gfloppy* per que no tens la disquetera al fstab, per editar-lo pots fer-ho mitjançant la consola:
```
sudo gedit /etc/fstab
```
això et preguntarà el password d'administrador (si ho ets, serà el mateix que el teu) i t'obrirà el gedit per editar l'arxiu, vigila com el modifiques, et recomano que et facis una copia abans de l'arxiu.
Assegura't a més de que el diretori */media/floppy* existeixi, si no existeix, fes:
```
sudo mkdir /media/floppy
```
En principi no has de tenir cap més problema

---

### Post by prostata on 2007-05-29
> **crazyserver said:**
> Suposo que no et funciona el *gfloppy* per que no tens la disquetera al fstab, per editar-lo pots fer-ho mitjançant la consola:
```
sudo gedit /etc/fstab
```
això et preguntarà el password d'administrador (si ho ets, serà el mateix que el teu) i t'obrirà el gedit per editar l'arxiu, vigila com el modifiques, et recomano que et facis una copia abans de l'arxiu.
Assegura't a més de que el diretori */media/floppy* existeixi, si no existeix, fes:
```
sudo mkdir /media/floppy
```
En principi no has de tenir cap més problema

T'adjunto el que diu l'ajuda de feysti fawn, però malgrat tot al clicar amb el botó dret no surt l'opció formatar: alguna sugerència??


"Para formatear un disquete, pulse con el botón derecho en el objeto que representa el disquete en el escritorio, después elija Formatear. Se muestra un diálogo del Formateador de disquetes. Vea la documentación del Formateador de disquetes para más detalles."

---

### Post by crazyserver on 2007-05-29
M'ho he mirat i a mi tampoc em surt res de res i el gfloppy no em va ni res :S
Potser que tirem per un altra banda...la linia de comandes
Quan tinguis el disquet desmuntat, fes:
```
mkdosfs -F 16 /dev/fd0 
```
després del -F has de indicar el tipus de fat, 12, 16 o 32
mes més infomacio pots fer:
```
man mkdosfs
```
potser et cal posar *sudo* al davant

A veure si hi ha sort

---

### Post by prostata on 2007-05-29
> **crazyserver said:**
> Suposo que no et funciona el *gfloppy* per que no tens la disquetera al fstab, per editar-lo pots fer-ho mitjançant la consola:
```
sudo gedit /etc/fstab
```
això et preguntarà el password d'administrador (si ho ets, serà el mateix que el teu) i t'obrirà el gedit per editar l'arxiu, vigila com el modifiques, et recomano que et facis una copia abans de l'arxiu.
Assegura't a més de que el diretori */media/floppy* existeixi, si no existeix, fes:
```
sudo mkdir /media/floppy
```
En principi no has de tenir cap més problema

al directori /media tinc el seguent: disk que correspon al diskete, de fet puc veure el que hi ha. desprès hi han; floppy i floppy0 i per descomptat cdrom, però pel que m'interesa crec que el tema és als floppy....alguna altre sugerència??

gràcies

---

### Post by prostata on 2007-05-29
> **crazyserver said:**
> M'ho he mirat i a mi tampoc em surt res de res i el gfloppy no em va ni res :S
Potser que tirem per un altra banda...la linia de comandes
Quan tinguis el disquet desmuntat, fes:
```
mkdosfs -F 16 /dev/fd0 
```
després del -F has de indicar el tipus de fat, 12, 16 o 32
mes més infomacio pots fer:
```
man mkdosfs
```
potser et cal posar *sudo* al davant

A veure si hi ha sort
Ok he fet tal com dius i el diskette s'ha quedat net i pulit, però i per tancar el tema, ¿pots fer-me cin centims sobre aquestes dues sentencies que hem fet?? és per fer culturilla....Gràcies

PS, sempre será el mateix procediment per formatar diskettes oi?

---

### Post by CarlesOriol on 2007-05-29
en kde kfloppy

Insta&#320;les amb 

[INDENT]sudo apt-get install kfloppy[/INDENT]

i executes 

[INDENT]kfloppy[/INDENT]

---

### Post by prostata on 2007-05-29
Gràcies a la vostra col-laboració he descobert com resoldre el problema, que es troba al fil dues preguntes...
gràcies i espero que també sigui útil per a tothom

---

### Post by crazyserver on 2007-05-29
perfecte!
i en carlesoriol ho ha acabat de rematar ;)
[B]
mkdosfs [/B]crea un sistema de fitxers (formata) en format de DOS (FAT), la comanda genèrica és mkfs (que crea un sistema de fitxers linux, en la opcio -t especifiques el sistema de fitxers (ext2, ext3, reiserfs,...))

**man **és el manual de linux, qualsevol comanda sobre la que tinguis dubtes li preguntes al man, per exemple: man mkfs.

Espero que tot t'hagi servit per aprendre una mica més!

Per cert, ja de pas, si pots editar el titol del missatge original (el primer que has escrit i escriure, com has posat en aquest últim: **[RESOLT] formatar diskete-[dues preguntes]) **
Gràcies

---

### Post by orestesmas on 2007-05-29
Arribo tard... com sempre.

Només volia aportar que hi ha uns programets molt interessants que estan agrupats en un paquet que es diu "mtools". Són un conjunt d'ordres que comencen totes per la lletra "m" i que intenten emular les ordres de gestió de disc que hi havia a MS-DOS o FreeDOS. A més, funcionen les lletres d'unitat.

Per exemple, per llistar els continguts d'un disquet es faria:

mdir a:          (no cal muntar-lo)

I per formatejar-lo es faria

mformat a:

Ordres potser només aptes per a nostàlgics, però que a mi em van treure de més d'un embolic quan començava amb GNU/Linux.

Ara acabo de veure també que hi ha una versió "gràfica"

mtoolsfm - a graphical user interface for accessing dos formatted floppies

Pots provar-ho. Si més no és curiós.

Orestes.

---

### Post by prostata on 2007-05-30
> **orestesmas said:**
> Arribo tard... com sempre.

Només volia aportar que hi ha uns programets molt interessants que estan agrupats en un paquet que es diu "mtools". Són un conjunt d'ordres que comencen totes per la lletra "m" i que intenten emular les ordres de gestió de disc que hi havia a MS-DOS o FreeDOS. A més, funcionen les lletres d'unitat.

Per exemple, per llistar els continguts d'un disquet es faria:

mdir a:          (no cal muntar-lo)

I per formatejar-lo es faria

mformat a:

Ordres potser només aptes per a nostàlgics, però que a mi em van treure de més d'un embolic quan començava amb GNU/Linux.

Ara acabo de veure també que hi ha una versió "gràfica"

mtoolsfm - a graphical user interface for accessing dos formatted floppies

Pots provar-ho. Si més no és curiós.

Orestes.

Oreste, he instal-lat amb synaptic el  mtoolsfm però un cop fet no el trobo per en lloc, i fet un ceerca per aquest criteri i tanpoc el veig...¿alguna sugerència??, al ser gràfic jo l'esperava veure'l per eines del sistema ¿?
gràcies

---

### Post by orestesmas on 2007-05-30
Ignoro si queda col·locat en el menú. A vegades amb els programes que no són de cap escriptori concret passa que no queden posats al menú, perquè l'autor de paquet "passa" de configurar-ho per cadascun dels escriptoris existents.

Potser l'hauràs de col·locar a mà.

Per executar-lo, jo obriria un terminal i teclejaria "mtoolsfm", a veure què passa. Si no passa res, serà que el nom de l'executable no és aquest. Aleshores en el mateix terminal tecleja:

dpkg -L mtoolsfm |grep bin

i et donarà una llista dels fitxers executables que conté el paquet. Algun d'ells serà al principal.

Orestes.

---

