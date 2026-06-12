---
title: "Tengo este mismo problema!!! - Configurar resolucion de la placa de video"
date: 2008-01-30
forum: Argentina Team
---

### Post by RaulCBA on 2008-01-30
Hola les comento que tengo este mismo problema...

[http://ubuntuforums.org/showthread.php?t=639435&highlight=resolucion](http://ubuntuforums.org/showthread.php?t=639435&highlight=resolucion)

Como hago para poder configurar bien la resolucion de la pantalla sin tener que desactivar la aceleracion 3d????
Gracias por la ayuda!!!

---

### Post by clasificado on 2008-01-31
¿y probaste con la misma solución?
```
sudo dpkg-reconfigure xserver-xorg
```

Tecnicamente, el archivo **/etc/X11/xorg.conf** tiene las configuraciones sobre resoluciones. Ahi habria que buscar las que tienen permitido tu monitor (resolution), y la que virtualmente trata de emular (virtual).

clasificado

---

### Post by RaulCBA on 2008-01-31
Hice la prueba de cambiar la virtual poniendole 1024x768, pero resulta que cuando hago eso la pantalla se agranda pero no se ajusta a los limites de la pantalla y tengo que desplazar la pantalla con el mouse, o sea que no veo todo el contenido de la pantalla en mi monitor. No se si se me entiende...
Probe con "sudo dpkg-reconfigure xserver-xorg" y me deja elegir todas las resoluciones pero sin activar la aceleracion 3D... Como lo hago??? Y como se si la aceleracion esta activada??? Tengo entendido que si tiro glxinfo y me sale "direct rendering: yes" significa que esta activada, es asi? Por favor corriganme ni estoy equivocado. Muchas gracias!!

---

### Post by clasificado on 2008-01-31
Sea como fuere, te recomiendo ir de a pasos.

1) El virtual causa el efecto que describís. Deberia ser el limite maximo que tu monitor soporta, o el limite maximo que te gustaria usar. Si te jode el efecto, sacalo.

2) Lo importante del **dpkg-reconfigure xserver-xorg**, es que puedas cambiar bien de resoluciones segun tu hardware (monitor + placa de video). 

Si quedaron lo primero y lo segundo, lo tercero sale como piña

3) Aceleración gráfica: **direct rendering: yes** es la forma corta de decir que tenes aceleración. Si te dice que no, deberias lidiar con tu placa de video (segun si es nvidia o ati, cada uno tiene su forma)

clasificado

---

### Post by RaulCBA on 2008-02-01
Te comento: tengo una GeForce2 GTS7Pro de 32 Mb... el problema de las resoluciones lo solucione con dpkg-reconfigure xserver-xorg. Elijo los drivers nvidia (no los nv) que supuestamente son los que permiten la aceleracion y cuando me pide colocar el tipo de monitor pongo basica... Reinicio y todo muy lindo, con todas las resoluciones disponibles... pero cuando tiro glxinfo me sale el famoso "core dumped" al final y la linea donde tendria que aparecer "direct rendering: yes" no aparece. Voy a apariencia para ver si puedo activar los efectos de escritorio pero me sale que no se pueden activar los efectos... En conclusion, no puedo activar la aceleracion con todas las resoluciones (cuando esta activada solo me permite 800x600 y 640x480). Ya no se me ocurre que modificar!!!!!

---

### Post by clasificado on 2008-02-01
Ahi vamos mejor. Osea que de las resoluciones nos olvidamos.

**¿Como instalaste el driver de nvidia? ** Los drivers propietarios pueden instalarse de mil maneras diferentes: Repositorios, Scripts, Envy, Automatic, El bin oficial, etc. Puede que tengas que reinstalarlo, y lo mejor seria saber de donde venis para decirte hacia donde ir.

¿Que es eso del "core dumped"? **¿Podrias postear acá la salida de la consola que le corresponde?** Puede ser famoso allá por el continente de los NVIDIA, pero para los que tenemos ATI hay un océano en el medio :P

clasificado

---

### Post by RaulCBA on 2008-02-02
Instale los de la pagina oficial de nvidia, los de los repositorios, con envy... de todas esas formas me pasa lo mismo! Despues de instalarlos de cualquier forma, hay que realizar otra operacion? Cuando este en mi maquina posteo lo que me tira el glxinfo... jeje esto me tiene loco!!! Gracias por toda la ayuda!!!

---

### Post by ariel on 2008-02-02
Si instalaste el driver propietario de nvidia, proba abrir desde el menu de aplicaciones:

System Tools > NVIDIA X Server Settings

Deberias ver todas las resoluciones disponibles y ahi podes cambiar la reso. en el momento.

---

