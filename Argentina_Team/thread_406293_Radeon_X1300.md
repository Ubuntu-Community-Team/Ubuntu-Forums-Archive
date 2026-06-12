---
title: "Radeon X1300"
date: 2007-04-10
forum: Argentina Team
---

### Post by backstab on 2007-04-10
Hola amigos soy nuevo en el foro pero no en ubuntu lo  use por unos años con mi vieja maquina con la cual no tuve problemas y siempre investigando logre lo que me propuse.
Esta vez no puedo lograr el bendito direct rendering YES. Estoy usando la version 6.10 Alguien tiene algun problema similar? es posible lograr la aceleracion? les paso la config de mi maquina por si sirve de algo. el sonido anda perfecto. pude configurar la coneccion a internet manualmente. lo unico que me falta es la aceleracion para despues poder hacer andar el beryl.
les agradezco de antemano cualquier ayuda que me puedan dar.

Procesador: Core 2 duo 6300
Motherboard: Msi 975X Power Up Edition
Memoria: 1 GB ddr2 667Mhz corsair
Rigido: Western Digital 160 GB Sata II
Grabadora de DVD Pioneer 16x Dual layer
Video: Saphire Radeon 1300X 128MB HM

---

### Post by backstab on 2007-04-10
pueden borrar el post ya lo solucione

---

### Post by marianom on 2007-04-10
Se le escribió al usuario para confirmar si desea que borremos el post o si es posible que publique la solución a su problema.
El thread queda a la espera de confirmación.

---

### Post by backstab on 2007-04-12
Asi es como solucioné el tema de la aceleración en la Ati Radeon X1300 siguiendo un tutorial que encontre por ahí. Esto lo hice en una instalación limpia de Ubuntu Edgy Eft 6.10. lo que tiene de bueno es que son todos comandos y se hace rapido. 

Abrir terminal y poner:

sudo gedit /etc/X11/xorg.conf

Poner estas lineas al final del archivo de texto que se abre guardar los cambios y cerrarlo:

Section "Extensions"
Option "Composite" "Disable"
EndSection

Seguir con estos comandos en la terminal:

sudo apt-get update

sudo apt-get install linux-restricted-modules-$(uname -r)

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

Reiniciar la maquina y listo.

Saludos!

---

### Post by Benji86 on 2007-04-12
Si pones Composite "Disable" cuando intentes levantar Beryl/Compiz me parece que no te va a tirar (emerald por lo menos no).
Ojo, hablo desde mi expreciencia con NVIDIA yo pero...

---

### Post by backstab on 2007-04-12
lo voy a usar en XGL al beryl y dicen por ahí que con XGL y ATI tiene que estar disable

---

