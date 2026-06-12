---
title: "Otro Error En Synaptic"
date: 2007-10-20
forum: Argentina Team
---

### Post by marcesneibrun on 2007-10-20
ante todo gracias por ayudarme, el synaptic cuando lo quiero recargar me tira este error:

W: GPG error: [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) gutsy-updates Release: Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

alguna idea para solucionarlo

gracias

---

### Post by clasificado on 2007-10-20
Empezá probando con esto, y volve a actualizar

```
gpg –keyserver wwwkeys.eu.pgp.net –recv-keys 40976EAF437D05B5
apt-key add ~/.gnupg/pubring.gpg
```

Clasificado

---

### Post by steve_ignorant on 2007-10-20
a mi me tira este error... lo posteo entero
 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


si alguien sabe como arreglarlo o en todo caso y mejor dicho, "como configurarlo" lo agradeceria mucho.

---

### Post by tzulberti on 2007-10-20
El mensaje mismo te dice como solucionarlo:
dpkg --configure -a

Como necesitas permisos de admin, necesitas hacer sudo dpkg --configure -a.

---

### Post by steve_ignorant on 2007-10-20
si lo que yo no sabia era que si habia que configurarlo manualmente, o se hacia solo... por eso en el post aclare. igualmente gracias. 

ahora me desaparecen la barras de titulo de las ventanas y se me pegan arriba...

---

### Post by tzulberti on 2007-10-20
A que te referis con que se pegan arriba?
Eso de que desaparecen las barras de las ventanas no es la primer vez que lo habia escuchado. Podrias poner una captura de pantalla

---

### Post by WanderingKnight on 2007-10-20
> 
ahora me desaparecen la barras de titulo de las ventanas y se me pegan arriba...

Proba:

```
metacity --replace
```

---

