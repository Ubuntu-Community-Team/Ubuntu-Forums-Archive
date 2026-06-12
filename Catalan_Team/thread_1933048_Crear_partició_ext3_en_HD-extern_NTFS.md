---
title: "Crear partició ext3 en HD-extern NTFS"
date: 2012-02-28
forum: Catalan Team
---

### Post by jinglada on 2012-02-28
Adjunto imatges del GParted del HD-extern NTFS muntat i no muntat. Veureu que muntat sembla tot correcte amb la informació de la partició /dev/sdb1 on es veu l'espai utilitzat i no utilitzat, en canvi quan no està muntat, el GParted no detecta l'espai utilitzat i el no utilitzat i la informació de la partició /dev/sdb1 dona:
ERROR: Filesystem check failed
ERROR: 5875 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NTFS by this software until it gets repaired.

Que hauria de fer per reduir la /dev/sdb1 a unes 675 GiB i crear una particio ext3 de 256 GiB?

[http://ubuntuforums.org/album.php?albumid=2466&pictureid=8356](http://ubuntuforums.org/album.php?albumid=2466&pictureid=8356)
[http://ubuntuforums.org/album.php?albumid=2466&pictureid=8357](http://ubuntuforums.org/album.php?albumid=2466&pictureid=8357)

L'àlbum de les imatges és: [http://ubuntuforums.org/album.php?albumid=2466](http://ubuntuforums.org/album.php?albumid=2466)

---

### Post by jinglada on 2012-02-28
Ara he aconseguit enganxar els fitxers d'imatge :-)

---

### Post by wgarcia on 2012-02-29
Jo crec que el que t'està dient és correcte, el disc té errors a la taula d'assignació i per tant el gparted no pot fer modificacions perquè s'arriscaria a perdre dades. T'ho diu quan està desmuntat perquè és quan pot fer modificacions.

Això sols es podria arreglar corregint aquests errors, però com el volum és NTFS això no es pot fer des de Linux (això ho hauria de mirar una mica més, no estic del tot segur que no es pugui fer des de Linux) i et recomana fer-lo des d'un sistema Windows.

---

