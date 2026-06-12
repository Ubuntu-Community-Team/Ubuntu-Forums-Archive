---
title: "Open office no anda!"
date: 2007-07-20
forum: Argentina Team
---

### Post by nachito on 2007-07-20
Buenas... deje de usar ubuntu un tiempo y cuando entro no anda mas ningun programa del open office!! 
Aparece la pantallita de bienbenida del open office y luego nada!!
Alguien puede ayudarme? =D

---

### Post by marianom on 2007-07-20
Correlo desde la terminal para ver que error da.

ejemplo:

```
ooffice -calc
```

---

### Post by nachito on 2007-07-20
bueno y me tira este error :

[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav aldx failed!

terminate called after throwing an instance of 'com::sun::star::uno::RuntimeExce ption'

/usr/lib/openoffice/program/soffice: line 233:  7605 Cancelado               "$s 

d_prog/$sd_binary" "$@"

** (process:7592): WARNING **: Unknown error forking main binary / abnormal earl y exit ...

---

### Post by marianom on 2007-07-20
Parece tan feo como genérico.
Yo diría que...
1- desinstales y reinstales el OO (desde Synaptic deberías poder resolverlo con unos pocos clicks)
2- si eso no funciona, cargues un bug en [Malone]("https://bugs.launchpad.net/").

---

### Post by nachito on 2007-07-20
bueno ya lo reinstale y me sigue tirando el mismo error :S

a lo mejor si lo actualizo se arregla porque no se muy bien estod e reportar bugs

---

### Post by marianom on 2007-07-20
no estoy seguro que diferencia habría entre actualizar y reinstalar el paquete.

¿Tenés cuenta de Launchpad? De ser así, te creo yo el bug si querés (te podes asociar al bug así te llegan los mails de seguimiento) y lo vamos viendo. Obvio te pido que estés atento si piden más pruebas ya que yo no voy a poder replicarlo.

Avisame.

---

### Post by nachito on 2007-07-20
Bueno... mira ya me registre y toy reportando un bug, pero donde dice "package" q pongo?,
porque pongo "open office" y dice q no existe ese paquete, tendre q poner el nombre exacto del paquete? como el que me sale en el synaptic?

EDIT: ya esta ya lo reporte...

---

### Post by kowal on 2007-07-21
Acá dan con una solución:

[http://ubuntuforums.org/showthread.php?t=173566](http://ubuntuforums.org/showthread.php?t=173566)

```
sudo chown -vR <usuario> /home/<usuario>/.openoffice.org2
```

---

### Post by nachito on 2007-07-22
Gracias!!!!!!!!!!!!!!! :)
 ;)

---

