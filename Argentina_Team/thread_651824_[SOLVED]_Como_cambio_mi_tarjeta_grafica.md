---
title: "[SOLVED] Como cambio mi tarjeta grafica?"
date: 2007-12-28
forum: Argentina Team
---

### Post by atari130xe on 2007-12-28
Gente, acabo de cambiar la tarjeta gràfica (reemplacè mi vieja TnT2 M64 de 32 MB por una Gforce 6200 de 128MB), el problema es que no se como actualizar el controlador para esta tarjeta. O sea cuando inicio el sistema entro con el viejo controlador y se ve totalmente borroso y practicamente no se distingue nada. Alguien podria explicar paso por paso por favor, como arreglar este cambio y poder utilizar la nueva tarjeta? muchas gracias!

PD: Uso Ubuntu Gutsy.

---

### Post by User21 on 2007-12-28
Antes que nada, deberias intentar desactivar los drivers desde el gestor de controladores restringidos, si es que alli estan activados, en el menu Sistema > Administracion. Cuentanos que sucede..!

Sino, ingresa a Pantallas y Graficos, en el mismo menu, e intenta resolverlo desde el alli!

---

### Post by atari130xe on 2007-12-28
> **User21 said:**
> Antes que nada, deberias intentar desactivar los drivers desde el gestor de controladores restringidos, si es que alli estan activados, en el menu Sistema > Administracion. Cuentanos que sucede..!

Sino, ingresa a Pantallas y Graficos, en el mismo menu, e intenta resolverlo desde el alli!

Gracias por tu respuesta pero como dije, NO PUEDO VER NADA en pantalla, està totalmente ilegible lo que aparece en el monitor. Alguna otra sugerencia? (gracias!):(

---

### Post by User21 on 2007-12-28
Antes que nada, hacerle un backup al archivo xorg.conf desde cualquier consola (Alt+F1,por ejemplo)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.copia
```
Luego intenta,reconfigurar xorg:
```
 [SIZE=-1]**sudo dpkg**-**reconfigure** xserver-xorg[/SIZE]
```[SIZE=-1] 
y configura paso a paso las diferentes secciones, a conciencia, especialmente las de GRAFICA. Si no sabes que poner, lee con detenimiento que te dice. Suerte! 
[/SIZE]

---

### Post by hernan blau on 2007-12-28
Aquí encontré esto que te puede servir: [http://www.ubuntu-es.org/index.php?q=node/74056](http://www.ubuntu-es.org/index.php?q=node/74056)
Suerte

---

### Post by valucha on 2007-12-28
[COLOR="DarkOrchid"]Yo te recomiendo que reinstales todo... Para asegurarte de no tener problemas... Por más que se peuda solucionar sin reinstalar siempre es bueno tenerlo bien desde el principio ^^[/COLOR]

---

### Post by rojojuan on 2007-12-28
Te digo como hice yo:
Instalé un programa que se llama Envy. Lo podés bajar de aquí.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Lo instalás.
Inmediatamente después inicias Envy y elegis la oción de eliminar todo driver.
Después de eliminado, elegís la opción isntalar el nuevo driver.
Esta opción hace que Envy vaya a la página de Nvidia y te instale el nuevo driver.
Hace todo lo necesario para dejarte todo ok.
Ultimamente cambié el viejo driver por el nuevo y seguí los pasos que te comento. Todo bien.

Espero que te sirva

---

### Post by atari130xe on 2007-12-28
> **valucha said:**
> [COLOR="DarkOrchid"]Yo te recomiendo que reinstales todo... Para asegurarte de no tener problemas... Por más que se peuda solucionar sin reinstalar siempre es bueno tenerlo bien desde el principio ^^[/COLOR]

Traté con el "reconfigure" pero nada, (cuando digo "nada" es que no reconocía la tarjeta gráfica) así que como la instalacíon era reciente no habia mucho backup para hacer, reinstalé el OS desde cero y ahora está todo funcionando de 10.
Graciassss

---

### Post by User21 on 2007-12-28
Ponele [SOLVED] al post, desde el menù Thread Tools ! Suerte.

---

