---
title: "Recuperar arvchivos"
date: 2008-02-12
forum: Argentina Team
---

### Post by h9005 on 2008-02-12
Buenas resulta que el ·$%$·&%$&$%&%$ de mi hermano borro de una particion ntfs con windows funcionando archivos de vital importancia, y no he recuperado algunos ya que ni aparecen en la lista. Con el recuperador de windows no puedo verlos ya, hay algo que pueda correrse desde linux?

---

### Post by faktorqm on 2008-02-13
Hola, creo que ya no tiene solución, no deberias haber hecho eso si no preguntar primero, ahora ya esta, te cuento para la proxima:
En cada particion, existe una carpeta que se llama ".Trash-nombredeusuario". Por ejemplo mi carpeta se llama ".Trash-faktorqm". En GNU/Linux, todos los archivos y/o carpetas que comienzan con punto, significa que son ocultos. En lugar de ser un atributo como en windows directamente aca se modifica el nombre.
Todos los archivos que borro tu hermano automaticamente se mueven a esa carpeta, para recuperarlos, o bien ponias restaurar en la papelerita que aparece abajo a lderecha si no la cambiaste de lugar, recuperar y ya.
Obviamente, si apreto SHIFT + SUPRIMIR no fue a parar a la papelera, pero te avisa igual. 
Para ver las carpetas ocultas en el Nautilus, apreta CTRL + H. en consola, ls -a. Salu2!!

---

### Post by h9005 on 2008-02-13
Estaba corriendo Windows cuando lo hizo, no creo que lo mismo lo mande a esas carpetas. O sea en linux no hay recuperador de archivos borrados?

---

### Post by faktorqm on 2008-02-14
AAAAAHHHHHHHHHHHHHHHHHHHHHH pense que estaba en linux ............. con razon! que yo sepa no hay un recuperador de archivos de windows en gnu/linux. salu2!

---

### Post by marianom on 2008-02-14
1er tema: el fraticidio es un crimen especialmente virulento y la marca de Caín nunca se te borrará: respira profundo, viaja al Tibet y en 7 años volvé renovado y en paz.

2do tema: ¿probaste con un LiveCD de una distro que esté especializada en soft forense? No tengo experiencia específica pero es posible que puedas bootear de un LiveCD y usar alguno de los programas que trae para recuperar algo. [Este]("http://www.e-fense.com/helix/") es el primero que encontré en el buscador más popular.
Ponete la campera de CSI y hacele un tiro, perdido por perdido da lo mismo.

---

### Post by juanman on 2008-02-14
Aca te paso un link con varias herramientas de linux para recuperar datos perdidos: [http://www.bairesnortelug.com.ar/2007/01/31/recuperacion-de-datos-perdi-todo-y-ahora-que-hago/]("http://www.bairesnortelug.com.ar/2007/01/31/recuperacion-de-datos-perdi-todo-y-ahora-que-hago/")

Proba el Photorec (q esta pensado para fotos pero sirve para otros tipos de documentos mas), q esta en los repositorios de ubuntu, tenes q instalar el paquete testdisk...
Tambien esta el trinity rescue kit es un live cd q trae varias herramientas, entre ellas el ntfs undelete...

Suerte y conta como te fue...

---

