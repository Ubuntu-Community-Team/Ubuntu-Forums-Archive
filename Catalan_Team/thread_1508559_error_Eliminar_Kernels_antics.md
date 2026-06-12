---
title: "error Eliminar Kernels antics"
date: 2010-06-13
forum: Catalan Team
---

### Post by diablessamariken on 2010-06-13
Hola

em van recomanar que anés esborrant els Kernels antics de tant en tant per alliberar espai al disc.

Segueixo aquests passos 

```
sudo dpkg -l | grep linux-image
```
```
sudo apt-get remove --purge KERNELAELIMINAR 
```

(en el lloc de KERNELAELIMINAR hi poso la versió del Kernel adequada eh)

però al final del procés m'apareix el següent error.

```
rmdir: failed to remove «/lib/modules/2.6.24-25-generic»: Directory not empty

```

Em podeu dir què he de fer perquè funcioni bé?

Gràcies!

---

### Post by epileg on 2010-06-13
Després de cercar «linux-image», jo faria una cerca amb el número de versió a eliminar, en el teu cas ```
sudo dpkg -l | grep  2.6.24-25
```, i deprés eliminaria tots els packets que inclouen aquesta versió al nom, tal com ```
sudo apt-get purge linux-headers-2.6.24-25 linux-headers-2.6.24-25-generic linux-image-2.6.24-25-generic
```

Salut.

---

### Post by wgarcia on 2010-06-13
Una altra possibilitat és anar a Sistema -> Administració -> Gestor de paquets Synaptic i marcar els paquets del nucli que vols eliminar.

---

### Post by diablessamariken on 2010-06-29
gràcies! ho provaré des del Synaptic!

Astrid

---

