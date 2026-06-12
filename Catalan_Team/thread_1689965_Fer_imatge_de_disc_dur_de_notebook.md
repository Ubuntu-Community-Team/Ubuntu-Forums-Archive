---
title: "Fer imatge de disc dur de notebook"
date: 2011-02-17
forum: Catalan Team
---

### Post by Curial on 2011-02-17
Hola a tots,

Acabo d'estrenar un notebook i voldria, abans d'instal·lar l'Ubuntu, fer una imatge del disc dur que ve amb les dues particions, una per al windows7 i l'altre per recuperació d'aquest SO.(és un HP).

De fet voldria fer-la sense fer servir una disquetera externa,(no en tinc) passant la imatge a una memòria usb, cosa que no sé si és possible.

Gràcies.

Salut.

---

### Post by kukat on 2011-02-20
Amb disquetera externa supose que et referiràs a una unitat CD-ROM...XDDD

Bé, a GNU/Linux tens la comanda "dd". 

És la comanda que utilitza el Partimage (que va amb Live CD). 

Ací hi ha una guia prou fàcil: [http://doc.ubuntu-es.org/index.php?title=Clonar_discos_duros](http://doc.ubuntu-es.org/index.php?title=Clonar_discos_duros)

Però bé, és senzill:

sudo dd if=/dev/hda of=/dev/hdb bs=1M

/dev/hda -> disc a clonar
/dev/hdb -> on es guardara.

---

### Post by tanreb20 on 2011-02-23
EL problema d'aquesta comanda és que fa la imatge de TOT el disc... i si el disc es molt gran... Fa una ISO inmensa...

Hi ha una opcio per fer la ISO de tan sols la part ocupada?

---

### Post by kukat on 2011-02-23
Sip!!! Amb el partimage:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

De fet crec que és el mateix programa que el "dd" però amb eixa característica. 

De totes formes, als Hiren's Boot hi ha diverses ferramentes per a fer imatges del disc dur. 

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)


Però en compte. Jo provaria la imatge després de fer-la......

---

### Post by kukat on 2011-02-24
Altra opció que hi ha és fer la còpia amb "dd", com he dit abans, i després fer una super compressió mitjançant el bzip2. 

SI no el tens instal·lat és tan senzill com

```
sudo apt-get install bzip2
```

Una vegada realitzada la imatge amb el "dd", fas el següent:

```
bzip2 -9 fitxer_imatge  
```

I ja està, tindràs una imatge comprimida i preparada per a guardar.

[font]("http://www.backuphowto.info/linux-backup-hard-disk-clone-dd")

---

### Post by kukat on 2011-02-24
Ja sabia jo que es podrien combinar les dues coses!! :D

Ací t'expliquen com fer el que he dit, però simultàniament: 

[http://kutxa.homeunix.org/howtos/backup_fs.html](http://kutxa.homeunix.org/howtos/backup_fs.html)


que gran és GNU/Linux!

---

### Post by kukat on 2011-02-24
Bé, he fet una còpia de seguretat de la partició "/home" del portàtil . 

La partició era de** 225 GB:**

linux-y5l8:/home/jordi # ```
time dd if=/dev/sda4 | bzip2 --best > /media/wickerman/backupjordi.bz2  
```

471865344+0 registres llegits
471865344+0 registres escrits
241595056128 octets (242 GB) copiats, 11453,2 s, 21,1 MB/s

real    190m53.513s
user    157m46.548s
sys     15m31.958s


Ha tardat 190 minuts a realitzar-se (utilitzant la màxima compressió). He realitzat la còpia a un disc dur extern (/media/wickerman) 


El fitxer generat ocupa 13,2 GB!!! XDDD 
No està gens malament.

---

### Post by Curial on 2011-02-28
Ostres, molt interessants tots aquests enllaços.

Tinc material per uns quants dies.


Moltíssimes gràcies kukat.

Salut.

---

### Post by kukat on 2011-03-01
Açò és una bona alternativa per fer una imatge del disc dur per tindre un sistema que no canvia. 

Però si tens que fer còpies diàries, incrementals i altres coses, hi ha altre alternatives...entre elles de codi tancat i de pagament, com el Acronis True Image Server o el Ghost. Sobretot el primer, que et permet fer còpies incrementals i altres coses (bé, el ghost no sé si també permet fer-ho). 

A GNU/linux hi ha altres alternatives com el PING (Partimage is Not Ghost) 

Després tens el sistema de còpies de seguretat tradcional, que a GNU/Linux tens el BACula, que pinta molt bé.

---

