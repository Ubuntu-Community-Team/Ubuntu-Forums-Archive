---
title: "Ayuda para erradicar Win2"
date: 2007-12-03
forum: Argentina Team
---

### Post by Mauro22 on 2007-12-03
Buenas!! :)


Hoy un dia especial para mi. 
Despues de un largo camino, a veces complicado, estoy usando linux en un 100%, olvidandome de aquello llamado win2. (Algunos programas con el win2 virtualizado, pero eso no cuenta)



Mi situación:
Tengo dos discos IDE, 80Gb con Windows, y 160Gb con linux y partición fat. GRUB.


Como seria para borrar win2, dejar ese disco en fat o ext3? Formateo el disco y saco la opcion del GRUB??
Como hago para que directamente entre en ubuntu? (sin tener que tocarlo)


Sé que hacen esto de onda nomás, asi que desde ya muy agradecido a cada uno que lee/responda.

Sin más,.-

---

### Post by faktorqm on 2007-12-04
hola, olvidate de sistemas de archivos de m$ xD
te conviene ext3 para lo que supongo la vas a usar vos. Yo lo que recomendaria (asi lo tengo yo en mi casa) en el disco de 160gb, hace una de 10gb como "/" primaria formateada a ext3, otra de swap (el tamaño es el doble o cuatro veces tu memoria RAM) y hace 2 particiones con lo que te queda de espacio, tambien formateadas a ext3. una la pones como /home, la otra como /media/datos (por ejemplo).
Con el disco de 80gb, depende de vos, yo crearia una sola ext primaria en /media/datos2 (en casa le puse "dos", "tres", etc)

Con el grub tenes ke editar el archivo menu.lst, dicho en criollo:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bkp
```
```
sudo gedit /boot/grub/menu.lst
```

si nunca lo tocaste, te vas a dar cuenta solo mediante los comentarios que aparecen ahi que es cada cosa. si tenes "miedo" de sacar algo y queres probar, antes de borrar algo comentalo. si la bardeas bajate el "super grub disk".
para entrar directamente a ubuntu en ese archivo fijate la entrada que dice "default", y al lado tiene un numero, 0 para la primera opcion, 1 para la segunda, etcetc

si tenes dudas avisa. salu2!

---

### Post by Mauro22 on 2007-12-04
La cosa es que no quiero desinstalar ubuntu. Lo tengo andando joya y costó como para borrar todos los discos y cargarlo de cero.

A menos que haya algo que me permita hacer una copia exacta de mi ubuntu y asi si formatear todo.


Se puede formatear el disco de XP, y sacar todas las opciones del GRUB?

---

### Post by Moonlit Knight on 2007-12-04
Instalá el gparted y de ahí particioná el disco de 80 y después tendrías que editar el fstab para hacer que te monte la unidad, y lo del grub fijate ahí dice como editar.

Saludos

---

### Post by faktorqm on 2007-12-06
mira, desde la teoria (vi gente de este foro que hizo), simplemente con copiar el contenido de la particion en una nueva, y actualizar el grub, es suficiente, no hace falta reinstalar.

si no estas seguro por algun motivo, podes agarrar un programa que saque imagenes, tipo norton ghost o simil, y sacarle una imagen, y actualizar el grub. salu2!

---

