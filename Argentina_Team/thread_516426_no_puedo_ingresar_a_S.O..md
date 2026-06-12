---
title: "no puedo ingresar a S.O."
date: 2007-08-03
forum: Argentina Team
---

### Post by marcesneibrun on 2007-08-03
Hola Voy A Tratar De Ser Lo Mas Breve Posible, Trate De Instalar El Beryl En Ubuntu 7.04, Se Me Colgo La Maquina, Yo Tengo En Mi Compu Instalado Tanto El Ubuntu 7.04 Como El Windows Xp.
Cuando Enciendo La Compu Entra A Una Pantalla Q Me Da Varias Posibilidades Entrar A Windows En Forma Segura, Automatica, Etc, Ya Probe Todas Las Posibilidades Q Me Da `para Ingresar A Windows Y La Maquina Lo Unico Q Hace Es Reiniciarse Una Y Otra Vez Sin Poder Ejecutar Windows, Wn Wl Caso De Ubuntu Ni Siquiera Me Aparece La Opcion Para Ingresar En él.
Necesitaria Me Ayuden
Gracias Marcelo

---

### Post by gepatino on 2007-08-03
Proba de iniciar con el cd de instalacion, en modo rescate. Una vez que tengas disponible una consola, hace lo siguiente:

monta la particion donde tenes ubuntu. suponiendo que es /dev/hda2 (cambiala por lo que corresponda):

mount /dev/hda2 /mnt

haces un chroot a ese directorio:

chroot /mnt

reinstalar el grub (gestor de arranque):
grub-install


despues de esto reinicia la máquina de forma limpia:

suhtdown -r now
o
init 6

luego de bootear deberias ver el menu de grub con las opciones de booteo.

si windows sigue sin iniciar, no te puedo ayudar porque no tengo experiencia con ese sistema, pero a menos que se haya dañado el disco, deberias poder ingresar a ubuntu.



PD: solo por curiosidad... tenés algún plugin que te ponga la primer letra de cada palabra en mayúsculas? si no es así... que paciencia :)

---

### Post by valucha on 2007-08-03
> **gepatino said:**
> Proba de iniciar con el cd de instalacion, en modo rescate. Una vez que tengas disponible una consola, hace lo siguiente:

monta la particion donde tenes ubuntu. suponiendo que es /dev/hda2 (cambiala por lo que corresponda):

mount /dev/hda2 /mnt

haces un chroot a ese directorio:

chroot /mnt

reinstalar el grub (gestor de arranque):
grub-install


despues de esto reinicia la máquina de forma limpia:

suhtdown -r now
o
init 6

luego de bootear deberias ver el menu de grub con las opciones de booteo.

si windows sigue sin iniciar, no te puedo ayudar porque no tengo experiencia con ese sistema, pero a menos que se haya dañado el disco, deberias poder ingresar a ubuntu.



**PD: solo por curiosidad... tenés algún plugin que te ponga la primer letra de cada palabra en mayúsculas? si no es así... que paciencia :)**
[COLOR="DarkOrchid"]
Offtopic: me parece que si escribís todo con mayúsculas (todas las letras) se te cambia y ponbe de esa forma.[/COLOR]

---

### Post by gepatino on 2007-08-04
Probando Si Valucha Tiene Razon :)

(no Me Iba A Quedar Con La Intriga) ;)


Edición: Gracias al groso que hizo este plugin!!  =D>

---

