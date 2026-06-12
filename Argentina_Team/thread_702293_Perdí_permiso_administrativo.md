---
title: "Perdí permiso administrativo"
date: 2008-02-20
forum: Argentina Team
---

### Post by aregnando on 2008-02-20
Hola a todos, ayer mientras trataba de corregir un problema en Opera, toqué algo en la "Editar Usuarios y Grupos" que hizo que quede como un usuario sin ningún tipo de posibilidad de administrar el sistema, tanto así que me desaparecieron del menú sistema>administración, todas las opciones que tienen ese fin (Synaptic, Origenes del software, etc.) incluso en terminal no me permite utilizar el comando "sudo".
Necesito un alma caritativa ya que esta vez la hice buena, je je.
Creo que metiendo la pata se aprende ¿no?

---

### Post by Mauro22 on 2008-02-20
Podes loguearte como root??

---

### Post by aregnando on 2008-02-20
Hola Mauro22, no lo se, nunca lo he hecho, siempre he logueado como el usuario por defecto y no tenía problemas, ayer lo único que hice fue instalar Firestarter y luego como quería copiar un archivo desde una carpeta a otra en la cual no me dajaba copiarlo, entré al módulo de editar usuarios y grupos, hasta donde se no toqué nada vital.
Estoy en este momento como un usuario sin ningún privilegio administrativo por tanto no puedo cambiar nada.
Como verás soy bastante nuevo en Ubuntu y hay infinidad de cosas que aún desconozco, estuve buscando en google si había algo referido a esto pero no encontré nada y ya estoy entrando en pánico.

---

### Post by Mauro22 on 2008-02-20
Fijate si podes entrar a la consola y poner:

sudo passwd

primero te va a pedir tu password y luego vas a poder ingresar el de root. (En ubuntu viene vacio por defecto)

Luego, cerras la sesion y como nombre de usuario pones root y como contraseña la que escribiste recien


Asi tendras acceso a todo el sistema, despues vas a Sistema -> Administar -> Usuarios y Grupos


seleccionas tu usuario (no root) y le das en propiedades, luego en previlegios de usuario y activas las que te parezcan correctas.
(Yo tengo todas activadas, menos la 4, la 6 y la ultima)

Cerras sesion y abris normalmente la tuya.

[B]
No uses nunca la cuenta root por mucho tiempo y si es posible sin acceso a internet.[/B]

---

### Post by aregnando on 2008-02-20
Hola Mauro22, el sistema no me deja realizar ninguna acción con sudo, estoy totalmente bloqueado para administrar, incluso desapareció el ícono del disco rígido que suele estar en el escritorio y por supuesto no tengo acceso a la partición en la que está windows por tanto no puedo leer nada de la misma.
No tendrá nada que ver el hecho de haber instalado Firestarter? 
Es como si intencionalmente hubiera entrado y hubiera sacado todos los privilegios administrativos que tenía mi usuario, cosa que por supuesto no hice o no me percaté de que de alguna manera lo estuviera haciendo.
Muchas gracias por tu ayuda.

---

### Post by Mauro22 on 2008-02-20
Si te animas, me queda una cosa por intentar. (Imprimilo si te parece)


Tenes Grub?? Espero que si

> 
Lo mas facil es entrar por grub en modo "single": 
 
- Al bootear la maquina, en el menu de grub, sobre la opción de Ubuntu presiona la tecla "e" . Te va a mostrar las diferentes opciones que tienes de booteo, selecciona la que dice algo como "kernel /algo" (no me acuerdo exactamente como se llama, lo estoy escribiendo de memoria). Presiona nuevamente la letra "e" y escibe al final de la linea la palabra "quiet" (sin comillas). Despues le das un enter para confirmar los cambios y despues apretas la letra "b". Con esto te bootea en single mode. Te toparás con la consola: digita ahi passwd . Ahí puedes cambiar la contraseña de root. Luego reinicia y deshace los cambios que hiciste a grub.


Esto lo saque del foro de ubuntu-cl.

Al iniciar en modo "single" el sistema es monousuario, en modo consola con todos los privilegios.


Desde ahi hace lo de passwd, le das una contraseña a root y reinicias normalmente.
En la pantalla de bienvenida pones root como usuario y las password que inventaste antes.

Sino te deja entrar (si no tenes activado el login de root) hace:

Control + Alt + F1

y pones root y la contraseña, luego startx, si te da error al querer inicar X, haces 

rm /tmp/.X0-lock  (Ese archivo aparece en la exlicacion del error que te tira.
Despues de borrarlo, haces startx, y en modo grafico, haces lo del post anterior (Lo de usuarios y grupos)



Avisame!

---

