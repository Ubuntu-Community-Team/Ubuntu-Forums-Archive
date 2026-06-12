---
title: "[SOLVED] particio ntfs"
date: 2007-06-23
forum: Catalan Team
---

### Post by sianeu on 2007-06-23
He muntat un nou disc dur, i vull escriure en una partició ntfs. L'he muntat amb:

sudo mount -t ntfs /dev/sdb2 /media/particiodades

Tinc instal·lat el ntfs-3g i el punt de muntatge a /media. Sembla que s'ha muntat, però sensa permisos, NI DE LECTURA. La icona de la carpeta a /media està amb una creu vermella a sobre i em diu que no tinc permís. Les particions ntfs que ja hi eren quan vaig instalar ubuntu, sí son accessibles i s'hi pot escriure.

Què he fet malament?  Cóm s'arregla?

Salut

PD: Al fstab no hi surt. Podria crear la linea al estil de les altres ntfs:

# Entry for /dev/sda6 :
UUID=248C94298C93F390 /media/sda6 ntfs-3g defaults,locale=ca_ES.UTF-8 0 1

El problema es que no se el valor de UUID

---

### Post by AlexMuntada on 2007-06-23
```
sudo vol_id /dev/sda6
```

---

### Post by sianeu on 2007-06-24
Gracies. Ja tinc la UUID, però el truqui no ha funcionat. Desprès de escriure la linea al fstab i reiniciar, ni tan sols detecta bé el tamany de la partició. Si torno a repetir la ordre de muntatge, torna a detectar bé el tamany, però altre cop sens permisos. Al reiniciar (i tornar a agafar el fstab) torna a detectar malament el tamany (però molt malament: de 350Gb a 430Mb). 

Alguna cosa està molt malament :D

No te importància, perque ja fa dies que he decidit reinstalar el sistema i aprofito per fer proves i instalar i provar programes.....  però qualsevol suggeriment será ben rebut.

Salut

PD: M'he donat conta que els 430Mb que ara em dona d'espai la particiò a /media son en realitat el espai que queda lliura a la partició arrel (??????).... Com si no estès muntada i la carpeta fos una carpeta qualsevol dins /.

---

### Post by AlexMuntada on 2007-06-24
Executeu això, però canviant **sda1** per la vostra partició NTFS:

```
ls -ld /mnt
sudo mount -t ntfs-3g /dev/sda1 /mnt
df -h /mnt
ls -ld /mnt
echo foo > /mnt/foo.txt
cat /mnt/foo.txt
sudo umount /mnt
```

Indiqueu-nos tot el que heu escrit i el resultat; així veurem si funciona bé l'ntfs-3g i què cal posar a l'fstab.

---

### Post by sianeu on 2007-06-24
No ha anat gaire bè per manca de permisos, si no era això el que s'havia de veure ho torno a repetir amb "sudo" devant...

sianeu@unicorn:~$ ls -ld /mnt
drwxr-xr-x 2 root root 48 2006-12-20 18:51 /mnt
sianeu@unicorn:~$ sudo mount -t ntfs-3g /dev/sdb2/mnt
Password:
Ús: mount -V                 : mostra la versió
    mount -h                 : mostra aquesta ajuda
    mount                    : llista els sistemes de fitxers muntats
    mount -l                 : ídem, incloguen les etiquetes de volumen
Fins aquí la part informativa. Seguim amb el muntatge.
El comandament és `mount [-t tipus_sis._fitx.] alguna_cosa lloc'.
Els detalls en /etc/fstab es poden ometre.
    mount -a [-t|-O]         : munta tot l'indicat en /etc/fstab
    mount dispositiu         : munta el dispositiu en el lloc conegut
    mount directori          : munta el dispositiu conegut aquí
    mount -t tipus disp dir  : comandament mount ordinari
Tingueu en compte que no muntareu realment un dispositiu, sinó més
aviat el seu sistema de fitxers (el tipus donat). També es pot muntar
un arbre de directoris ja visible en un altre lloc
    mount --bind dir_antic dir_nou
o moure un subarbre:
    mount --move dir_antic dir_nou
Es pot donar un dispositiu mitjançant el nom, posem-hi /dev/hda1 o
/dev/cdrom o mitjançant l'etiqueta, usant -L etiqueta o mitjançant uuid,
usant -U uuid. D'altres opcions: [-nfFrsvw] [-o opcions].
Per a més detalls, escriviu man 8 mount.
sianeu@unicorn:~$ df -h /mnt
S. fitxers            Tamany En ús Lliure %Ús Muntat a
/dev/sda2             6,9G  6,5G  435M  94% /
sianeu@unicorn:~$ ls -ld /mnt
drwxr-xr-x 2 root root 48 2006-12-20 18:51 /mnt
sianeu@unicorn:~$ echo foo > /mnt/foo.txt
bash: /mnt/foo.txt: Permission denied
sianeu@unicorn:~$ cat /mnt/foo.txt
cat: /mnt/foo.txt: No such file or directory
sianeu@unicorn:~$ sudo umount /mnt
umount: /mnt: No està muntat

---

### Post by AlexMuntada on 2007-06-24
> **sianeu said:**
> No ha anat gaire bè per manca de permisos, si no era això el que s'havia de veure ho torno a repetir amb "sudo" devant...

sianeu@unicorn:~$ ls -ld /mnt
drwxr-xr-x 2 root root 48 2006-12-20 18:51 /mnt
sianeu@unicorn:~$ sudo mount -t ntfs-3g /dev/sdb2/mnt
Password:
Ús: mount -V                 : mostra la versió
...

Justament per això us demanava que escriguéssiu les ordres i el resultat: us heu deixat un espai entre **/dev/sda2** i **/mnt** ;)

Podeu repetir-ho però posant-hi l'espai que falta?

---

### Post by sianeu on 2007-06-24
Ho sabia, estic avergonyit. Haurè de tenir una seriosa xarrada amb el meu subconcient, perque a més es de les poques vegades que no faig un sencill copy/paste  :(

Repeticiò de la jugada:

sianeu@unicorn:~$ ls -ld /mnt
drwxr-xr-x 2 root root 48 2006-12-20 18:51 /mnt
sianeu@unicorn:~$ sudo mount -t ntfs-3g /dev/sdb2 /mnt
Password:
sianeu@unicorn:~$ df -h /mnt
S. fitxers            Tamany En ús Lliure %Ús Muntat a
/dev/sdb2             456G  106G  351G  24% /mnt
sianeu@unicorn:~$ ls -ld /mnt
drwxrwxrwx 1 root root 4096 2007-06-23 20:36 /mnt
sianeu@unicorn:~$ echo foo > /mnt/foo.txt
sianeu@unicorn:~$ cat /mnt/foo.txt
foo
sianeu@unicorn:~$ sudo umount /mnt
sianeu@unicorn:~$

---

### Post by AlexMuntada on 2007-06-24
Bé, així doncs sembla que us funciona bé: la mida del disc és correcta i podeu escriure-hi sense problemes (la prova és l'arxiu foo.txt de la partició).

Només caldrà que executeu el **vol_id** per a saber l'UUID del sda2 i adaptar convenientment l'arxiu fstab.

---

### Post by sianeu on 2007-06-24
Ara no funciona el vol_id

sianeu@unicorn:~$ sudo vol_id /dev/hdb2
Password:
/dev/hdb2: error open volume

No he tocat res des de l'acciò anterior.

Avans d'aquestes últimes accions havia repetit aquesta ordre més d'un cop i comprovat que sempre sortia el mateix valor.....  Alguna cosa ha canviat.

---

### Post by AlexMuntada on 2007-06-25
Diria que sí heu tocal alguna cosa: si més no, ara poseu **/dev/hdb2** enlloc de **/dev/sdb2** ;)

---

### Post by sianeu on 2007-06-30
Perdò per l'error, tot i que em sembla que a estat al escriure el missatge. El cas es que ja havia desconectat el disc dur i borrat la linea del fstab.

Al tornar-ho a provar de nou, fent servir el "NTFS configuration tool" me l'ha activat per escritura sensa cap problema. No se que devia passar.

Moltes gracies per la teva ajuda.

Salut

---

