---
title: "Necesito guia para VNC Server."
date: 2007-09-03
forum: Argentina Team
---

### Post by verahert on 2007-09-03
Hola, como veran es mi primer Thread, el tema es el siguiente, estuve probando infinidades de guias en la web para levantar vncserver pero no lo logre, si alguien es tan amable de pasarme una guia que funcione se los agradeceria por ahora estoy usando freenx pero necesito poder compartir sesiones.

Desde ya muchas gracias.

Saludos.

---

### Post by Hei Ku on 2007-09-03
Hay un par de maneras distintas para instalar vnc.
Por empezar, si tenes el de 64 bits, es un poco mas complicado porque el paquete de ubuntu estaba roto la ultima vez que me fije.

Segundo, lo que vos queres es compartir la sesion con el que se loguea en la maquina, o compartir la sesion con otros que se loguen remoto?
Si es el primer caso, creo que lo mejor es el X11vnc, que es un addon de VNC para el X. 

Tercero, los how-tos son distintos, dependiendo de si usas Ubuntu o Kubuntu.

---

### Post by verahert on 2007-09-03
Lo que yo quiero es algo similar al Remote Desktop de MS, no se si me explico, me logueo con usuario pepe por remote y queda logueado en esa pc si voy fisicamente a esa pc esta pepe logueado con su sesion corriendo, si yo ahora voy desde el remote y me logueo como jorge, voy a esa pc y ahora esta jorge logueado con su sesion corriendo, es decir desplazo a pepe. 

Tengo version 32bits.

Saludos.

---

### Post by nest on 2007-09-03
La verdad es que no entiendo lo que querés hacer porque en mi vida use el Remote Desktop de MS. Pero acá tenés un tuto para aprender a instalar Real VNC y otros posibles proggies para correr remotamente el escritorio como si estuvieses en esa máquina.

[How-To]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_desktop_or_VNC_host_from_a_Ubuntu.2FLinux_machine")

Si era otra cosa lo que buscabas, avisa y te trato de ayudar.

---

### Post by verahert on 2007-09-03
Jaja, lo que es la comunicacion :P, es muy simple cuando yo inicio sesion remotamente es como si estuviese iniciando sesion realmente sentado en la pc, cuando salgo del remote me queda bloqueado la pc con esa sesion corriendo.  
Me parece que el x11vnc me sirve me pasan una guia (confiable) de como instalarlo?

Saludos.

---

### Post by nest on 2007-09-03
> **verahert said:**
> Jaja, lo que es la comunicacion :P, es muy simple cuando yo inicio sesion remotamente es como si estuviese iniciando sesion realmente sentado en la pc, cuando salgo del remote me queda bloqueado la pc con esa sesion corriendo.  
Me parece que el x11vnc me sirve me pasan una guia (confiable) de como instalarlo?

Saludos.

sé que no te gastaste en entrar al link que te pase.

en mi post anterior te explica paso a paso como habilitar en ubuntu un VNC y te da 3 opciones para descartar aplicaciones parar correr el VNC. Te aconsejo Real VNC, es el que usé y funcionó a la perfección.

saludos.

---

### Post by verahert on 2007-09-03
esa guia explica como configurar vino ya la habia hecho y no me funciono.

Saludos

---

### Post by nest on 2007-09-03
a no ser que no tengas router instalado o el puerto que estas usando para conectarte remotamente es imposible que no te funcione si hiciste lo que dice ahi y no te tira error.

si tenes router tenes que abrir el puerto del VNC en el router .

---

### Post by verahert on 2007-09-03
No, lo probe por la red pero habia hecho algo mal con el vino y el vnc, instale x11vnc y me funciona barbaro, el Realvnc no me servia por que no puede conectarse sino hay una sesion abierta en cambio el x11vnc si, tema solucionado muchas grcias por su ayuda.

Saludos.

---

