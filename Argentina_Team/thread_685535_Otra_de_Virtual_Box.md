---
title: "Otra de Virtual Box"
date: 2008-02-02
forum: Argentina Team
---

### Post by fedescha on 2008-02-02
 Estube buscando en los forums Argentina y Absolute Beginner y no encontre nada. Puede que no haya buscado bien, no se. El tema es el siguiente: no puedo iniciar WXP porque no tengo permiso para usar /dev/vboxdrv. Me pide que ingrese a dbox users group. No se como hacer. Sou el unico usuario de la pc y no tengo coneccion a internet.
Gracias,

---

### Post by jclevien on 2008-02-02
Probá el siguiente comando: 
chmod 666 /dev/vboxdrv

y reinicia el VirtualBox.

Si no funciona, entonces cambiale el grupo a /dev/vboxdrv, como dice el mensaje, por el grupo "vboxusers".

Todo esto como root (salvo el reinicio del VirtualBox).

Yo personalmente el VirtualBox no lo uso ni lo recomiendo más, tuve bastantes problemas con el, en un momento se produjo un error inesperado al ejecutar máquinas virtuales y listo, no pude hacer más que arrancarlas como root.

La gente de VB no supo que hacer con ese error (dicho por ellos).

Esto te digo porque si bien es un producto con una emulación muy rápida, hay ciertas inestabilidades y temas comerciales (soporte USB) que realmente hicieron que desistiera y cambiara por QEMU.

VMware tampoco es recomendable, por las mismas razones.

Espero que te sirvan estos comentarios.
Saludos.


Juan

---

### Post by ariel on 2008-02-02
System > Administration > Users and Groups

Click en "Manage Groups"

Vas a ver un grupo llamado "vboxusers"

Seleccionale y hace click en properties.

Agrega tu cuenta de usuario al grupo. Dale OK, close, close.

Hace un logout de gnome, y volve a entrar. Ahora vbox deberia funcionar.

---

### Post by fedescha on 2008-02-04
Gracias por los consejos. Despues les cuento. Buscando alguna solucion me entere de algunos de los problemas de vbox, asi que voy a ver como funciona, pero por las dudas estoy bajando QEMU. Vamos a ver que tal.
Saludos,

---

