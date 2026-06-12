---
title: "Compartir documents windows i ubuntu"
date: 2011-10-03
forum: Catalan Team
---

### Post by bratac on 2011-10-03
Hola,

he fet el canvi a l'ordinador d'una cosina meva, li he instal·lat ubuntu en paral·lel amb windows (com a període de transició) el dubte és, com es poden compartir els documents que hi ha al windows amb l'ubuntu. Ho dic per no duplicar documents i fer-li la transició més fàcil.

Gràcies per l'ajuda.

Fins ara

Alfred

---

### Post by dmartinez116 on 2011-10-03
Tens algunes opcions...

1.- Crear una partició en NTFS de manera que tant windows com linux puguen accedir a ella.
2.- Fer que windows siga una màquina virtual (virtualbox) i afegir-li una carpeta compartida (qualsevol sistema de fitxers, per exemple ext4) de manera que tant windows com linux podran accedir (esta es la que faig servir jo)

Ja ens contes.

---

### Post by akyra on 2011-10-04
Hola,

Entenc que ens referim al mateix ordinador treballant amb Windows i Ubuntu amb un doble arranc, i que la teva cosina té els documents dins una partició de Windows, sigui la del mateix sistema o una altre per dades.
Si és així, el que has de fer és muntar la partició de forma automàtica cada vegada que entras a ubuntu i que el usuari que té la teva cosina tingui permisos per llegir i escriure a la carpeta dels documents.

Si no ho tens instal·lat és posible que et facin falta eines de ntfs. Et deixo un link a on ho explica, però és molt senzill.
[http://geowworld.blogspot.com/2009/11/montar-particiones-ntfs-automaticas-en.html]("http://geowworld.blogspot.com/2009/11/montar-particiones-ntfs-automaticas-en.html")

Si es un altre ordinador haurias de compartir la carpeta.
També pots fer el que diu dmartinez116 de crear una partició ntfs, però crec que si ja ho tens tot a dins del mateix ordinador no caldria.

Salutacions.

---

### Post by bratac on 2011-10-13
Gràcies per la informació,

encara no he mirat cap de les opcions que m'heu proposat perquè no he tingut temps d'una banda ni l'ordinador de ma cosina per jugar-hi d'una altra. 

Estic parlant d'un ordinador amb doble arranc i no volia virtualitzar el windows perquè el seu home és topògraf i treballa amb Autocad i no volia tenir problemes de rendiments ni coses estranyes amb el programa.

Una mica la idea era si hi podia haver com una mena de carpeta compartida en la qual hi puguin posar tots els documents que ara mateix utilitzen amb windows per utilitzar-los també amb linux indistintament (almenys fins que s'acabi l'etapa de transició).

D'aquí a quinze dies procuraré anar a «jugar» a veure si podem fer-hi alguna cosa...

Gràcies per l'ajuda i us mantindré informats!

---

### Post by akyra on 2011-10-14
Hola

Si és dins del mateix ordinador només has  de navegar fins a trobar la carpeta dins la partició de Windows. D'aquesta manera no necesites fer cap compartició de res. Compartir tindria sentit amb ordinadors diferents, però sino, només et fas arrastras la carpeta que vulguis compartir a la barra esquerra del nautilus i ja està.

Ja diràs que tal t'anat.

Adeu

---

### Post by snoopo71 on 2011-10-14
> **bratac said:**
> Gràcies per la informació,

encara no he mirat cap de les opcions que m'heu proposat perquè no he tingut temps d'una banda ni l'ordinador de ma cosina per jugar-hi d'una altra. 

Estic parlant d'un ordinador amb doble arranc i no volia virtualitzar el windows perquè el seu home és topògraf i treballa amb Autocad i no volia tenir problemes de rendiments ni coses estranyes amb el programa.

Una mica la idea era si hi podia haver com una mena de carpeta compartida en la qual hi puguin posar tots els documents que ara mateix utilitzen amb windows per utilitzar-los també amb linux indistintament (almenys fins que s'acabi l'etapa de transició).

D'aquí a quinze dies procuraré anar a «jugar» a veure si podem fer-hi alguna cosa...

Gràcies per l'ajuda i us mantindré informats!



De fet, per entrar des de Ubuntu cap als fitxers de Windows només has de muntar la partició de Windows(i tenir els paquets necessaris com ntfs-3g i companyia) i per entrar des de Windows al sistema d'arxius de linux l'altre dia vaig trobar un freeware que es diu [ext2explore]("http://sourceforge.net/projects/ext2read/files/") (o ext2read) i pots entrar a les particions ext4 per llegir i copiar arxius!  

Apa, sort!

---

