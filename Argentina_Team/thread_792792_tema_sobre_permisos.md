---
title: "tema sobre permisos"
date: 2008-05-13
forum: Argentina Team
---

### Post by faktorqm on 2008-05-13
Hola! Tengo un problema con los permisos de mi usuario en la pc del trabajo. El tema es que intente un par de cosas para ayudar a uno que pregunto como apagar la pc sin poner la contraseña por consola y resulta que rompi todo. 

Comento lo que hice para que se guien mas o menos, primero fui a sistema -> administracion -> autorizaciones y me autorice a mi mismo a apagar el sistema y reiniciar el sistema. 

Luego fui y me agregue al grupo gdm con el comando "sudo adduser faktorqm gdm". Luego reinicie y ahi comenzó la debacle total... Resulta que cada vez que abro algo con el boton "desbloquear" me dice que ha ocurrido un error inesperado, pero no me muestra nada salvo el boton de aceptar.
Luego no me preocupe, pero en sistema -> administracion por ejemplo, el synaptic, origenes del software, controladores de hardware y ventana de entrada NO aparecen. Cuando voy a sistema -> preferencias -> menu principal aparecen destildados, los tildo, y al segundo se destildan solos... intente apretar cerrar mas rapido de lo que se destildaban pero no funcionó :P

Luego edite el /etc/sudoers con el visudo. Aca ya estaba jugado y en lugar de arreglarla la empeoré. Puse algo parecido a esto creo:
faktorqm boulder=(ROOT) /sbin/shutdown
algo asi era, no me acuerdo y no tengo ganas de buscar el post.

Cuando reinicie, chau, directamente no podia hacer sudo a nada, y no habia seteado la contraseña del root desde la instalacion, asi que estaba atado. Reinicie en modo recuperacion y puse la clave de root y reinicie y volvi a editar el sudoers (mas abajo lo pego) y quedo como esta< ahora. Ya puedo hacer sudo a todo y todo re bien y contento, pero se me rompio lo del boton "desbloquear" y no encontre manera de solucionarlo.

ejemplo, el network-manager. si hago "sudo network-manager" me lo abre con todo gris. y escucha esta: me logueo como root, hago asi no mas network-manager.... y aparece todo gris igual!!! casi me caigo de c**o...

Esto que pusieron de las policies no me gusta nada, antes era sudo y gksudo y punto. Ahora no se como solucionar el problema. :(

empiezo a postear la salida de los comandos a ver si me pueden ayudar aunque sea comparando por contenido :S

```
faktorqm@the-edge:~$ cat /etc/group
root:x:0:faktorqm
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:
ssl-cert:x:108:
lpadmin:x:109:
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
faktorqm:x:1000:faktorqm
sambashare:x:124:
faktorqm@the-edge:~$ cat /etc/sudoers 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
faktorqm ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
faktorqm@the-edge:~$

```

Aclaro que me saqué del grupo gdm, pero no me puedo sacar de apagar y prender la pc por que no me anda el boton de desbloquear. Estaria bueno que me posteen su "cat /etc/sudoers" para comparar con el mio, por que la linea que esta abajo de root la escribi yo. Bueno cualquier cosa me dicen y posteo mas comandos. Gracias por leer :D

---

### Post by eldragon on 2008-05-13
no se como lo hiciste, pero te quitaste de todos los grupos pertinentes.

para poder editar /etc/groups vas a tener que bootear desde un livecd.

monta tu particion root y edita el archivo /etc/group

quitate de root:

agregate a adm:
agregate a tu grupo
agregate a cdrom
agregate a audio
agregate a video
agregate a plugdev
agregate a lpadmin
agregate a admin
agregate a powerdev
agregate a pulse
agregate a pulse-access | agrega a root
agregate a pulse-rt | agrega a root
agregate a sambashare


eso lo hice mas o menos siguiendo mi propio archivo group

---

### Post by faktorqm on 2008-05-13
uuuhhhh y como hiciste para darte cuenta de eso? 
con el usuario root no me alcanza para hacer esos cambios?
me podrias postear tu sudoers a ver que hay? Gracias :D

---

### Post by euzkoarima on 2008-05-13
primero, por si te sirve, mi sudoers dice 

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

segundo, creo que el lío lo armaste con

> sudo adduser faktorqm gdm

En realidad eso se supone que te agrega al grupo gdm, pero se ve que alguna vez me mande una metida de pata parecida porque en mis anotaciones tengo lo siguiente

> adduser (y no useradd)
usermod para modificar, pero cuidado, hay que dar TODOS los grupos, a no ser que se use con -a
Ejemplo
usermod -a -G ungrupo sunuevousuario

Si mal no recuerdo use adduser y me saco de los otros grupos, pero como anoté tan poco (no anoté parametros usados, etc) no estoy seguro.

Saludos

---

### Post by faktorqm on 2008-05-13
Muchas gracias che! Salio andando todo. Lamentablemente no vi a tiempo el sudoers de euzko asi que mañana borro esa linea de mas que esta ahi. 
euzko: Vos decis que adduser te saca de todos los grupos, pero por ejemplo, cuando probe la solucion de eldragon use ese comando en los grupos que el me habia dicho. Habia uno que no me dejo, powerdev, me decia que no existia. 
Al final me puse con root, saque a faktorqm del grupo root, y lo agregue en los grupos que me dijiste y agregue a root tambien. Reinicie y automaticamente me mostraba todo como antes, el synatic, etc. y podia hacer sudo, y pude apretar desbloquear. :KS 
Asi que mañana miro el sudoers. MUCHAS GRACIAS A AMBOS!!! ^_^

---

### Post by euzkoarima on 2008-05-14
La verdad NO estoy seguro que adduser te saque de todos los grupos, pero me llamó la atención que vos lo usaste y tuviste problemas y yo tengo anotado que usándolo también tuve problemas similares a los tuyos. Lamentablemente no anoté todo como debería haberlo hecho, así no tendría dudas ahora. Pero bueh!
Según el man como vos los usaste NO te debería haber borrado nada.

Saludos.

---

