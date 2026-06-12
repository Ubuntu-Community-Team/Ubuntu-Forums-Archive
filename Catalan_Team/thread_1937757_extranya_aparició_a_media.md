---
title: "extranya aparició a /media"
date: 2012-03-08
forum: Catalan Team
---

### Post by jinglada on 2012-03-08
Salutacions, "salvadors informàtics"!

Estava fent una imatge d'un HD extern al HD extern que tinc de Backup etiquetat com a Dades i se'n va anar el llum. 
Al tornar a connectar, aquest HD Dades que apareixia sempre com a /media/Dades, apareix com a media/Dades_ i també apareix un media/Dades propietat del root així:

root@joan-laptop:/media/Dades# ls -la
total 2242584
drwx------ 2 root root         4096 2012-03-01 18:56 .
drwxr-xr-x 4 root root         4096 2012-03-08 17:55 ..
-rw-r--r-- 1 root root 250059349504 2012-03-01 18:57 image
-rw-r--r-- 1 root root          163 2012-03-01 18:57 logfile
root@joan-laptop:/media/Dades# 

però això no té cap mena de sentit ja que la partició de l'Ubuntu és de 37 GB i aquesta imatge en té 250.

joan@joan-laptop:~$ df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda6              37G   13G   22G  37% /
none                  2,0G  320K  2,0G   1% /dev
none                  2,0G  3,2M  2,0G   1% /dev/shm
none                  2,0G  128K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/sda7             201G  188G  2,2G  99% /home
joan@joan-laptop:~$ 

Ho puc esborrar connectat com a root?

Gràcies a la bestreta!

---

### Post by Daerun on 2012-03-14
Sense el disc conectat ves a mirar a /media, a veure si la carpeta Dades (o la Dades_) pulula per allà; i efectivament, esborra-la. Compte, que a mi em va passar una cosa semblant, i després d'esborrar la dita carpeta Dades_ se'm tornava a crear automàticament, però no recordo com vaig arreglar això últim. No vol dir que t'hagi de passar, només ho dic perquè no t'estranyis si passa.

---

### Post by jinglada on 2012-03-14
> **Daerun said:**
> Sense el disc conectat ves a mirar a /media, a veure si la carpeta Dades (o la Dades_) pulula per allà; i efectivament, esborra-la. Compte, que a mi em va passar una cosa semblant, i després d'esborrar la dita carpeta Dades_ se'm tornava a crear automàticament, però no recordo com vaig arreglar això últim. No vol dir que t'hagi de passar, només ho dic perquè no t'estranyis si passa.

Gràcies Daerun. L'he esborrada des del nautilus clicant "Mou a la paperera" però a la paperera no hi apareix. Llavors he recordat que a partir del hardy, la paperera estava a /home/usuari/.local/share/Trash; hi he anat i tampoc he trobat la carpeta *Dades* esborrada amb els dos fitxers, *image* i *logfile*; tanmateix en aquesta paperera hi he trobat una carpeta, a part de les carpetes *files* i *info*, amb un nom que no recordo, que contenia fitxers mp3 i l'he esborrada clicant "Mou a la paperera" i a la paperera actual tampoc hi apareix. On és la "paperera del nautilus"? O és que clicant "Mou a la paperera" des del nautilus s'esborra directament sense passar per la paperera?

He connectat el HD extern i es connecta com abans. Es a dir que el fil queda *SOLVED*

---

### Post by jinglada on 2012-03-14
> **jinglada said:**
> Gràcies Daerun. L'he esborrada des del nautilus clicant "Mou a la paperera" però a la paperera no hi apareix. Llavors he recordat que a partir del hardy, la paperera estava a /home/usuari/.local/share/Trash; hi he anat i tampoc he trobat la carpeta *Dades* esborrada amb els dos fitxers, *image* i *logfile*; tanmateix en aquesta paperera hi he trobat una carpeta, a part de les carpetes *files* i *info*, amb un nom que no recordo, que contenia fitxers mp3 i l'he esborrada clicant "Mou a la paperera" i a la paperera actual tampoc hi apareix. On és la "paperera del nautilus"? O és que clicant "Mou a la paperera" des del nautilus s'esborra directament sense passar per la paperera?

He connectat el HD extern i es connecta com abans. Es a dir que el fil queda *SOLVED*

Ara recordo que el nom de la carpeta amb els mp3 era *expunged*.

---

