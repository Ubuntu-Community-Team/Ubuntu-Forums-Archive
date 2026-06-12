---
title: "No Puedo Abrir Synaptic"
date: 2007-10-20
forum: Argentina Team
---

### Post by marcesneibrun on 2007-10-20
GENTE INTENTE INSTALAR UN PAQUETE LANGUAGE-PACK-ES, Y ME TIRO UN ERROR, AHORA NO PUEDO ENTRAR AL SYNAPTIC, TAMPOCO A AÑADIR Y QUITAR APLICACIONES, Y NO ME PERMITE INSTALAR NADA, DE NADA, LES PASO EL ERROR QUE ME TIRA PARA VER SI ALGUIEN PUEDE AYUDARME, DESDE YA MUCHAS GRACIAS

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.



MARCELO

---

### Post by WanderingKnight on 2007-10-20
Antes que nada, te pediria por favor que no uses mayusculas todo el tiempo, pareciese que estas gritando.

> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Si lees bien (aunque tenes que saber un poco de ingles) dice que tenes que correr "dpkg --configre -a". Entra a una consola y tipea:

```
sudo dpkg --configure -a
```

Y deberia arreglarse.

---

