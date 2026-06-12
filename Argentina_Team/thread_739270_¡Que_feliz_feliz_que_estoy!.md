---
title: "¡Que feliz feliz que estoy!"
date: 2008-03-29
forum: Argentina Team
---

### Post by --Lutari-- on 2008-03-29
Acabo de instalar Ubuntu :) Ahora estoy Descargando las Actualizaciónes. Todavia sigo sin poder creer todo lo que tiene.

MUchas gracias a todos los que me ayudaron con mis problemas

---

### Post by Mauro22 on 2008-03-29
Felicidades, amigo!


En poco te daras cuenta del tiempo que perdiste usando windows.


:guitar:

---

### Post by margori on 2008-03-29
Felicitacion y bienvenido.

---

### Post by santiagoward2000 on 2008-03-29
Bienvenido y mucha suerte!! :KS

---

### Post by MaReaDo^ on 2008-03-29
felicitaciones, cualquier cosa no dudes en preguntar

(yo conteste todos tus threads anteriores y ahroa veo que ya pudiste xd)

---

### Post by xpelaox on 2008-03-29
Bienvenido che!

---

### Post by valucha on 2008-03-29
[COLOR="DarkOrchid"]Genial :)...

Ahora podrías decirnos qué juegos usa tu hermano para ver si hay alternativas que le gustan o si se pueden usar en Ubuntu...[/COLOR]

---

### Post by MaReaDo^ on 2008-03-29
ya los puso en otro thread

el hitman no aclaro cual de los 4 es, pero todos funcionan, algunos mejor que otros, pero todos son jugables, algunos problemitas de sonidos o algunas texturas
el pes 2008 yo lo jueg funciona bastante bien
el fifa 08 simil los otros
y el nfs tambien

por ahi tenes que remplazar dlls y hacer cosas, pero son jugables todos, salvo que tu hermano sea muy exigente y le molesten errores minimos o algunos crashes :P


mas info en  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by --Lutari-- on 2008-03-29
Lo ultimo que me falta es poner a Windows como Sistema Operativo Por Defecto En GRUB para que no haya problemas :S

---

### Post by atatiducken on 2008-03-29
Felicidades y bienvenido amigo
Para modificar el inicio por defecto del Grub ingresa en una terminal 
 **sudo gedit /boot/grub/menu.lst**
y en ese archivo hay una linea q dice **default** q indica la opción  con la q inicia, por defecto esta en **0** q es la primera opción, si queres iniciar en win deberías contar en q lugar se encuentra y restarle 1

**Ubuntu** default 0
**Ubuntu recovery mode** default 1
**Memtest** default 2
**Otros sietmas ..** default 3
**Windows** default 4

saludos

---

### Post by InsektO on 2008-03-29
> **--Lutari-- said:**
> Lo ultimo que me falta es poner a Windows como Sistema Operativo Por Defecto En GRUB para que no haya problemas :S

Como alternativa a lo que pusieron en el post de arriba, podés ir a **Aplicaciones > Añadir y Quitar**. Luego en el menú desplegable de la esquina superior derecha **Mostrar** elegís **"Todas las aplicaciones disponibles"** y buscás algo que se llama "Administrador de Arranque" y lo instalás.

Una vez instalado, vas a poder acceder desde **Sistema > Administración > Administrador de arranque**. Ahí vas a poder elegir el SO por defecto, el tiempo de espera hasta cargar automáticamente algún SO, la lista disponible, etc.

Es básicamente lo mismo, pero con una (mucho más intuitiva) interfaz gráfica.

Saludos!

---

### Post by sajnox on 2008-03-29
Me sumo a la sugetencia de insekto, tambien lo podes instalar desde una consola ejecutando

```
sudo apt-get install startupmanager
```

---

### Post by margori on 2008-03-30
Hay una forma sencilla de arreglar la pantalla del GRUB.

Instalte el paquete startupmanager.

Te permite decidir cual es el SO por defecto y varias cositas más para mejorar la seguridad.

---

### Post by User21 on 2008-03-30
Ahora que estas TAN FELIZ, podes subir una foto al album de usuarios felices de Ubuntu! :P 
Mas info [**aqui**]("http://ubuntuway.wordpress.com/2008/03/23/iniciativa-ubuntu-usuario-feliz/").
:popcorn:

---

