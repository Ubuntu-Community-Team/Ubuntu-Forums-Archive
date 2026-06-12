---
title: "Problema con resolucion de pantalla."
date: 2008-04-29
forum: Argentina Team
---

### Post by wanchan on 2008-04-29
Hola comunidad, mi problema es el siguiente.
Al actualizar de Gutsy a Hardy, y cada vez que inicio ubuntu no me reconoce la placa de video nVidia 6200 FX (creo:confused:) y las dos resoluciones que tengo son de 640x480 y 800x600 (solo esas dos). Instale el nvidia-settings, al ejecutarlo me aparece el siguiente mensaje:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Me parece que dice que debo usar el driver NVIDIA X y que tengo que editar el archivo de congiguracion X  y luego ejecutar nvidia-xconfig como root, y reiniciar el servidor X.

Tengo que primero instalar el driver de mi placa? (bajandolo de la pagina de NVIDIA?).
Como hago para editar el archivo de configuracion X?

Saludos a todos!!!

---

### Post by Hernán-Amaya on 2008-04-29
probá con envy si no sabes como modificar el archivo. si con envy no podés instalar el driver pasanos el archivo xorg.conf, por las dudas hace un backup del archivito antes de tocarlo.

suerte!!

---

### Post by wanchan on 2008-04-29
Hola gracias por responder pronto, lo que hice fue ir al gestor de controladores y habilitarlo desde alli, ya que no estaba usando la placa.
Ahora otra pregunta, como hago para tener 4 escritorios, fui al plug in de Cube quise cambiar la cantidad de desktop pero no pude cambiarlo, esta con valor 1.

---

### Post by atatiducken on 2008-04-30
si tenes la barra de abajo de gnome (esa donde se minimizan las ventanas, estan los dibujitos de los escritorios a la derecha y la papelera), toca boton derecho sobre el cuadrado q representa al escritorio(uno chico abajo a la derecha), ahora anda a **preferencias** y en **numero de areas de trabajo** pone 4, con eso deberias tener 4 escritorios
saludos

---

### Post by faktorqm on 2008-04-30
Hola, tenes que usar una herramienta de configuracion que yo no conocia, me la presento Radhios en la flisol (gracias ;))

```
sudo displayconfig-gtk
```

con eso elegis el driver y el monitor, PERO no le des al boton test, al menos a mi no me anduvo, o sea, te muestra el test, le decis que esta ok, pero no te guarda la configuracion :(

Espero que te haya servido. Salu2!

---

