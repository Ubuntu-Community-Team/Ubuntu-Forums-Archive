---
title: "ayuda driver de video"
date: 2008-03-15
forum: Argentina Team
---

### Post by phxnd on 2008-03-15
hola que tal, gracias por leer jaja

bueno mi problemita es:
instale el driver de mi placa nvidia, que es una ge force 4 por paqetes de la siguiente manera

$ sudo aptitude install nvidia-glx nvidia-kernel-common
$ sudo nvidia-xconfig

y esta barbaro, pero me oculto lo qu e seria la barra de titulo del programa, que tiene el boton de cerrar minimizay blablabl, y ademas, cuando abro una consola, se me ve todo blanco!! =S

no hay alguna forma de editar las opciones del driver de video??

o dejenme su opinion haber que hago xD

saludos

---

### Post by phxnd on 2008-03-15
ya lo arrelge solo, es un error que trae el driver de nvidia y lo que tense uqe ahcer es agregarle esta linea Option "AddARGBGLXVisuals" "True" en la parte de screen en el archivo /etc/X11/xorg.conf

lo dejo x si a alguno le paso lo mismo xD

---

### Post by niko_3100 on 2008-03-16
lo tenes con compiz?? que placa de video es bien? Geforce 4 cuanto mas?? gracias!!!

---

### Post by faktorqm on 2008-03-17
che yo tengo una gforce 4 mx 400 y con esos drivers que pones ahi no me anduvo nada... estas seguro que usaste eso y no envy? salu2!

---

### Post by phxnd on 2008-03-18
tengo una ge force mx 4000 y si lo tengo con compiz

---

