---
title: "Problema formatejant disk USB"
date: 2018-11-21
forum: Catalan Team
---

### Post by lluisanunez on 2018-11-21
Hola, em podeu ajudar? Intento formatejar un USB on hi havia posat una imatge d'ubuntu studio. L'aplicació "disks" em dóna el següent error:
[IMG]http://cvfitxers.ub.edu/docs/100888/Selection_045.jpg[/IMG]

---

### Post by wgarcia on 2018-11-22
Sembla que el disc havia estat creat amb "dd" i s'ha escrit incorrectament la partició, amb la qual cosa ara les eines normals per esborrar la partició no funcionen. Possiblement ho pots arreglar netejant completament primer el disc, i després tornant a crear les particions. Primer pot provar "fdisk":

```
sudo fdisk /dev/sdb
```

"p" et mostrarà la taula de particions, i amb "d" pots esborrar les particions que vulguis. Si això no funciona pots provar d'esborrar tot el disc amb la perillosa ordre "dd" [**ADVERTIMENT: ordre perillosa, no apliqueu sense saber el que esteu fent**] , aquí sí que s'ha d'anar amb molt de compte de no donar el disc incorrecte perquè et pots carregar el disc dur de l'ordinador, per exemple:

```
sudo dd if=/dev/zero of=/dev/sdb bs=512
```

compte que "sdb" sigui realment el disc que vols esborrar. Aquesta última ordre queda sota la teva entera responsabilitat, "dd" vol dir "delete-delete-delete", és a dir carregar-se tot al disc, si ho fas al disc dur no es pot recuperar res (és una bona ordre per netejar un disc abans de llençar-lo si tens dades sensibles).

---

### Post by lluisanunez on 2018-11-22
Gràcies, Walter. "dd" era la paraula màgica que buscava

---

