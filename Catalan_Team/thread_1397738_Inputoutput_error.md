---
title: "Input/output error"
date: 2010-02-03
forum: Catalan Team
---

### Post by tanreb20 on 2010-02-03
HOla!

Tinc un disc dur extern, heredat d'un antic portatil.

Sempre m'havia donat algun que altre problema al copair o llegir arxius, pero avui he trobat que gairebé no hi ha informació!

hi havia moltes fotografies, documets etc.. i ara quan faig un ls em surt aixo:

[508][alorma:curs 2008 - 2009]$ ls
ls: en llegir el directori .: Input/output error
[509][alorma:curs 2008 - 2009]$ sudo ls
ls: en llegir el directori .: Input/output error
[510][alorma:curs 2008 - 2009]$ 


Alguan idea de perqué? O que puc fer-hi?

---

### Post by oriolsbd on 2010-02-04
Hola,

Executa la comanda següent:
```
ls -l /media
```

Per cert, quin format té aquest disc? Ext, fat, ntfs,...?

Salut!

---

### Post by tanreb20 on 2010-02-04
Bé ara ja está, ja qeu el vaig formategar tot, després d'un reinici que em va permetre accedir ala informació (a vegades no el montava bé).

de tota manera, el resultat del ls -l

```
[502][alorma:/]$ ls -l media/
total 20
lrwxrwxrwx  1 root   root       6 2010-01-29 14:56 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2010-01-29 14:56 cdrom0
drwx------ 10 alorma alorma 16384 2010-02-04 12:08 DISCU
[503][alorma:/]$ 

```

Ara és Fat32

---

