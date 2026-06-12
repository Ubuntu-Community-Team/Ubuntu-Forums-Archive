---
title: "dpkg"
date: 2007-10-22
forum: Catalan Team
---

### Post by grundt on 2007-10-22
Intento instalar les actualitzacions i em diu això:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I al escriure a la terminal:

 sudo dpkg --configure -a

em posa:

dpkg: s'ha produït un error en processar hpijs (--configure):
 El paquet està en un greu estat d'inconsistència - heu de
 reinstal·lar-lo abans d'intentar la seva configuració.
S'han trobat errors en processar:
 hpijs

Què he de fer??

---

### Post by papapep on 2007-10-22
El mateix missatge d'error t'ho diu. Executa a un terminal l'ordre:

```
sudo dpkg --configure -a
```

---

### Post by grundt on 2007-10-22
Bé, primer havia escrit l'ordre posant sudo al davant, ara al fer-ho com tu dius, em posa:

dpkg: la operació sol·licitada requereix privilegis de superusuari

Perdona, com es feia per ser superusuari.

---

### Post by papapep on 2007-10-22
Si, se m'ha oblidat posar-hi el sudo. Fes-ho així, no ho facis com a superusuari.

---

