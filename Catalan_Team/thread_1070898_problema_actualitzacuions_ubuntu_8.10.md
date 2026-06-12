---
title: "problema actualitzacuions ubuntu 8.10"
date: 2009-02-15
forum: Catalan Team
---

### Post by laxineta on 2009-02-15
Hola.
he instal·lat ahir mateix l'Ubuntu 8.10 i a l'hora d'actualilzar em surt: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Vinga, viam si algú em dona alguna idea del que puc fer per solucionar-ho

Merci!

---

### Post by oriolsbd on 2009-02-15
Hola, executa amb "sudo" el que et demana el missatge. És a dir:

```
sudo dpkg --configure -a
```

Després, torna a provar d'actualitzar.

Salut!

---

### Post by laxineta on 2009-02-17
fet i solucionat

Merci

;)

---

