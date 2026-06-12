---
title: "quilombo de discos"
date: 2007-10-20
forum: Argentina Team
---

### Post by ideafix on 2007-10-20
buenas gente, les comento la fantochada q me mande. Tenia el windows en la primera particion, xubuntu en la segunda, y despues venia el swap. Cree una particion entre la de windows y la de xubuntu, donde puse datos. Despues se me dio por reinstalar windows, obviamentee al diablo el grub. Y obviamente, no puedo recuperarlo por mas manual q lea ja. Por lo q vi, el / esta en /dev/hda3, 1 y 2 son las ntfs. Y como no quiero hacer la de siempre - reinstalar xubuntu - quiero ver si por una vez puedo restaurar el grub. Desde ya gracias

---

### Post by Mauro22 on 2007-10-20
[http://www.ubuntu-es.org/node/862](http://www.ubuntu-es.org/node/862)

Fijate ese, a mi me salvo cuando reinstale win2


Salu2

---

### Post by ideafix on 2007-10-20
Gracias, habia probado algo asi, pero me larga error al momento de instalar el grub. Se me hace q hay quilombo porq antes era dev/hda2 lo q referenciaba el grub para arrancar xubuntu, y ahora es hda3. Puede ser?

---

### Post by clasificado on 2007-10-20
> pero me larga error al momento de instalar el grub.

¡Ponè el error man! ¡Que sino estamos a ciegas!

(Como poder ser, puede ser)

clasificado

---

### Post by sajnox on 2007-10-20
Ideafix,

Seguramente [ESTA]("http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/") guia te puede ayudar.

Saludos,

---

### Post by javier-2714 on 2007-10-20
mira yo lo solucione con supergrub esta genial recuperas el boot de cualquier so 
te lo restaura como estaba yo lo bage en cd suerte:

[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by ideafix on 2007-10-20
> **sajnox said:**
> Ideafix,

Seguramente [ESTA]("http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/") guia te puede ayudar.

Saludos,

Ya estoy mas cerca ja. Me sirvio, ahora tengo el grub cuando prendo, pero cuando le doy a ubuntu, me larga error 17, que no puede montar la particion o algo asi.

> mira yo lo solucione con supergrub esta genial recuperas el boot de cualquier so 

sisi, lo tengo, pero automaticamente no pudo arreglar. Y la q se me ocurrio es editar el grub, pero no se como entrar a editarlo

---

### Post by javier-2714 on 2007-10-20
proba la opción arrancar gnu/linux directamente una vez que inicia xubuntu podes editar el grub .  sudo gedit  /boot/grub/menu.lst

---

### Post by ideafix on 2007-10-20
No puede. Larga el error 17 no se puede montar la particion, formato desconocido. Muestra que quiere montar la hda0,1. Por eso larga el error de q no reconoce el formato de la particion. Xubuntu esta en la hda0,2. Y perdon, pero me acabo de dar cuenta q el titulo del post esta mal, seria quilombo de particiones jaja

---

### Post by joseluis on 2007-10-20
como te dijero, el super grub puede arreglar el problema: [http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

### Post by ideafix on 2007-10-20
Estoy respondiendo desde Xubuntu!!! jaja. Es medio largo lo q hice, asi q voy a tratar de explicarlo

Como dije, tenia el grub al arrancar. Puse "e" para editar la linea de arrancar con xubuntu en modo de rescate. Ahi edite la linea que decia (hd0,1) cambiando 1 por 2. Hecho esto, aprete "b" para q boteara. Arranco y me largo una linea de comando como root. Entonces puse

> vim /boot/grub/menu.lst

una vez ahi cambie el arranq normal de ubuntu, la linea donde decia

> root            (hd0,1)
por
> root            (hd0,2)
luego reboot y aca estoy, otra vez en casa jaja.
Gracias a todos por sus respuestas!!!!!

---

