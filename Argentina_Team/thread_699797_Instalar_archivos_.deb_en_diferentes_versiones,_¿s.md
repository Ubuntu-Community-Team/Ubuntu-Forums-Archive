---
title: "Instalar archivos .deb en diferentes versiones, ¿se puede?"
date: 2008-02-17
forum: Argentina Team
---

### Post by atari130xe on 2008-02-17
Duda "existencial" :lolflag: : Es posible instalar un determinado programa en formato .deb creado para Ubuntu 7.04 en la 7.10? supongo que si (yo lo eh hecho) pero para confirmarlo, se puede hacer eso?, por una cuestión "lógica" deberia ser factible, me lo confirman?:)

---

### Post by Hei Ku on 2008-02-17
No hay una respuesta general. El problema principal son las dependencias.
Si el programa depende de otro programa o libreria en particular que no esta disponible para esa version, no vas a poder. O de cierta version de kernel, que no es la de tu version, etc.

En definitiva, si son programas simples, no deberias tener problema, y de hecho lo he visto como workaround mas de una vez. Pero en ningun caso es recomendable. Llegado a ese punto, yo lo compilaria desde el codigo.

---

### Post by clasificado on 2008-02-18
```
sudo dpkg --install --force PAQUETE
```

Pero estas pegando LEGO con LADRILLOS.
Te garantiza que se instala, pero... ¿estas seguro que solo queres instalarlo? ¿Seguro que no queres que funcione?

no te garantiza que se encastre (ejem... funcione). No verifica dependencias. No revisa paquetes incompatibles. No garantiza estabilidad en el sistema después de su uso. No garantiza una limpia desinstalación posterior.

Agarra paquete, instala paquete.

¿No seria mejor compilar?

clasificado

PD: Si no te queres arriesgar tanto, sacale el "--force" que ahi ya no es tan malo como la peste negra, sino que se parece mas al sarampión

---

### Post by Hei Ku on 2008-02-19
Otra cosa, si decidis seguir adelante con la chanchada.
(Yo te avisé... y vos no me escuchaste!! :lolflag: )

Antes de hacer un upgrade de version, acordate de desinstalar los .deb que hayas instalado de esta manera. Si no, podes tener problemas de dependencias cruzadas, entrar un deadlock, y tener que reinstalar directamente. Muchos de los problemas de upgrade son por cosas de este tipo. Lo mismo vale para cuando instalas algo compilando, pero en este caso puede ser una estaca en el corazon del apt-get, asi que se puede poner peor.

---

