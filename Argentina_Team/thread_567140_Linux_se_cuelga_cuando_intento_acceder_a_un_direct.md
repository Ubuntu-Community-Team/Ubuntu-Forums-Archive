---
title: "Linux se cuelga cuando intento acceder a un directorio"
date: 2007-10-04
forum: Argentina Team
---

### Post by charly gr on 2007-10-04
hola,     me parece que esto es raro, pero si alguien tiene alguna idea al respecto se los agradezco.


Linux se cuelga cuando intento acceder a un directorio de mi disco rígido. Es un directorio lleno de archivos .doc, de medio giga aprox.

Cuando intento entrar a través de Office, se queda procesandio y tengo que salir del directorio.

Si trato de entrar por la terminal, se cuelga y no puedo salir ni siquiera con CTRL-C, tengo que cerrar la ventana.

El resto del disco parece funcionar bien.

Copio más abajo el mensaje que apareció en una ocasión en la terminal.

Si alguien tiene alguna vía de acción para recomendarme, se la agradecería. ¿Algún defragmentador? ¿O será un problema del hardware? 

saludos!


Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447606] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length )"

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447735] ------------[ cut here ]------------

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447741] invalid opcode: 0000 [#1]

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447743] SMP

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447816] CPU:    0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447817] EIP:    0060:[<dc9b2b51>]    Not tainted VLI

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447818] EFLAGS: 00210286   (2.6.20-15-generic #2)

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447854] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447858] eax: 00000090   ebx: d8482000   ecx: 00200082   edx: 00000000

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447862] esi: d8482018   edi: d89cc898   ebp: c4c76c6c   esp: d54f3e40

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447865] ds: 007b   es: 007b   ss: 0068

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447869] Process nautilus (pid: 8901, ti=d54f2000 task=cefb3050 task.ti=d54f2000)

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447871] Stack: dc9bef28 dc9be26b dc9c0d6d 00000180 dc9bf078 d54f3ea8 00000000 00000018

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447879]        00000000 d8dc4680 00000000 00000000 c4c76c6c dc9b3edd d54f3e90 d54f3ebc

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447885]        d7dc6000 00000000 00000000 c4dc06e0 00000000 00000000 000280d2 c03a8fac

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447892] Call Trace:

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447909]  [<dc9b3edd>] ext3_htree_fill_tree+0xad/0x200 [ext3]

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447933]  [<dc9bd610>] ext3_permission+0x0/0x10 [ext3]

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447959 ]  [<dc9ac062>] ext3_readdir+0x112/0x640 [ext3]

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447971]  [copy_to_user+41/80] copy_to_user+0x29/0x50

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447987]  [anon_vma_prepare+29/224] anon_vma_prepare+0x1d/0xe0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.447998]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448010]  [vma_merge+326/464] vma_merge+0x146/0x1d0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448022]  [sys_mprotect+276/1408] sys_mprotect+0x114/0x580

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448036]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448040]  [vfs_readdir+148/176] vfs_readdir+0x94/0xb0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448050]  [sys_getdents64+111/192] sys_getdents64+0x6f/0xc0

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448062]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448085]  =======================

Message from syslogd@ubuntu at Thu Oct  4 12:21:42 2007 ...
ubuntu kernel: [  345.448087] Code: 44 24 10 78 f0 9b dc c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 0d 9c dc c7 44 24 04 6b e2 9b dc c7 04 24 28 ef 9b dc e8 bf 40 77 e3 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 f0 9b dc c7 44 24 04 6b

---

### Post by facundocorradini on 2007-10-04
Hola charly

solo dos aclaraciones: 1) no existen desfragmentadores para linux, pq usa un sistema de archivos completamente distinto que es mucho más efectivo y NO se fragmente nunca. (buscá en el foro que hace poco hablamos de esto)

2) no quiero q panda el cúnico, pero a priori me da la sensación de fallo del filesystem... pero esperá la respuesta de alguno de "los que saben la posta" así te guían, seguro tiene una solución.

slds

---

### Post by charly gr on 2007-10-04
gracias Facundo,     voy a ver lo que contás de la defragmentación. Y ya que estoy veo qué sería un fallo del files system, por las dudas. Creo que tengo algún backup (en algún lado!)

saludo

c.

---

### Post by Mauro22 on 2007-10-05
Hola !

Podrias intentar hacer un backup, borrar la carpeta y volver a copiar los archivos.
:lolflag:

---

### Post by faktorqm on 2007-10-08
hola, para solucionar/diagnosticar problemas de fs existe un programa que se llama fschk.

proba "fschk --help" o "man fschk" y ahi te va a tirar las opciones.

Yo te recomendaria que pongas la que haga algun examen exhaustivo del disco con reparacion automatica.

OJO!!!!!!!!!!!!!!: por que primero no te fijas de instalar el driver de ext3 en guindous, a ver si podes hacer un bkp por las dudas. y ahi despues te fijas de hacer lo de arriba. si tampoco podes acceder, bueno, tiralo a la suerte. (yo nunca perdi un solo archivo ;)) salu2 y conta como te fue!!

---

