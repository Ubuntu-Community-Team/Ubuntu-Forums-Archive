---
title: "Links a l'XP trencats"
date: 2010-01-31
forum: Catalan Team
---

### Post by JUSTERINI1 on 2010-01-31
Hola
Tinc instal.lat el Jolicloud en un netbook, com que pràcticament és un Ubuntú possiblement em podreu ajudar.
En l'escriptori, hi ha les tipiques carpetes: video,documents,fotografies,... on hi he posat un link a la homònima carpeta de la partició XP, i així tenir-ho tot ordenat. 
Després de crear els links i durant la mateixa sessió funciona perfectament, però en properes sessions, la cosa pot o no pot funcionar, la majoria de vegades em diu que el link està trencat per ex: "*No es pot utilitzar l'enllaç perquè la seva destinació, «/media/disk/Documents and Settings/JUSTERINI/Mis documentos», no existeix."* d'altres vegades no hi ha problema.
No ho entenc, algú em podria donar algun tipus de solució?

Gràcies.
Justerini

---

### Post by akyra on 2010-02-01
És possible que la partició no estigui muntada quan et dona el fallo?

---

### Post by JUSTERINI1 on 2010-02-01
Hola Akyra,
Tens raó, el problema és aquest, el link funciona si abans he accedit directament a la partició.
He estat buscant per la webi, però segueixo sense tenir idea de com fer que es munti a l'inici, si em podeu donar una pista intentaré arreglar-ho.
Gràcies

---

### Post by akyra on 2010-02-02
Hola Justerini,

Mirat aquest enllaç, és molt senzill, [http://www.guia-ubuntu.org/index.php?title=Montar_particiones]("http://www.guia-ubuntu.org/index.php?title=Montar_particiones")

Basicàment és fer:
1.- Editar l'arxiu /etc/fstab
   > $ sudo gedit /etc/fstab
2.- Afegim aquesta linia, si no existeix, l'afegim al final, i si existeix s'haurà de modificar:
    > /dev/<particion> /media/<carpeta_montaje> <sistema_archivos> defaults 0 0

Crec que et quedaria així (hauràs de mirar quin nom de partició tens sda?? o hda?? normalment, depen dels discs durs que tinguis, i el tipus de sistema de fitxers NTFS o fat32 normalment):
> /dev/sda??? /media/disk/Documents and Settings/JUSTERINI/Mis documentos ntfs defaults 0 0

Ja ens diràs si t'anat bé.
Adeu

---

### Post by JUSTERINI1 on 2010-02-21
Hola
Disculpeu el retràs en la resposta.
Al final me n'he sortit, vaig començar com em recomanà l'Akyra, però alguna cosa no acabava d'anar bé, la instrucció que vaig posar i totes les seves variants tenien algun tipus d'error.
Buscant documentació a la web finalment he optat per instal·lar el "ntfs-config" i li he demant muntar la partició al punt "media/disk", et voilà!
al etc/fstab la iinstrucció ha quedat com: 

/dev/sda1 /media/disk ntfs-3g defaults,locale=ca_AD.UTF-8 0 0

A partir d'aquí cada vegada que inicio, començo amb la partició de l'XP muntada i tots els links que hi apunten preparats per funcionar.

Gràcies novament.
Justerini.

---

