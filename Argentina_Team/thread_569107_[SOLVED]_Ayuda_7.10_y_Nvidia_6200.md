---
title: "[SOLVED] Ayuda 7.10 y Nvidia 6200"
date: 2007-10-06
forum: Argentina Team
---

### Post by Mauro22 on 2007-10-06
Como andan?

Espero que mejor que a mi.




Les cuento, hasta ayer disfrutaba de un hermoso y estable ubuntu 7.10, tenia compiz fusion, awn, en fin todo para que quede lindo :)


A la noche, me salto una actualizacion disponible del kernel y los kernel-headers, entre otros.
Como de costumbre, acepte, los bajo, instalo y pidio que reinicie


Tras reiniciar, salio un cartelito que dice que ubuntu esta corriendo en una baja resolucion y que se debe a que mi monitor o mi placa de video no esta correctamente instalada. 
Seleeciono como pantalla un panel generico de 1280x1024 LCD
y placa Nvidia 6 Series, 

Y da error al entrar al modo grafico.

Una y otra vez...


Alguna ayudita

---

### Post by leo_rockway on 2007-10-07
yo particularmente tengo que usar el driver privativo de mi ati (porque el libre no funciona para nada). cada vez que cargo un nuevo kernel tengo que reinstalarle los drivers privativos de nuevo si no me levanta el vesa. quizas puede que a eso se deba tu problema.

---

### Post by DuckMan on 2007-10-07
cuando elijas el kernel en el grub, elegi la version anterior, hay un bug con la nueva q tienen q solucionar

cuando actualizen el kernel de nuevo, podes usar la nueva

---

### Post by Mauro22 on 2007-10-07
> ok, Gracias! 

Seguiré usando el kernel anterior

EDIT: El kernel anterior tampoco funciona :(, sin Ubuntu por el momento

---

### Post by DuckMan on 2007-10-07
q te dice?

---

### Post by Mauro22 on 2007-10-08
Levanta el modo grafico, pero no se "VE" son todas lineas de colores, y el logo de ubuntu por todos lados :mad:


Saludo

---

### Post by faktorqm on 2007-10-09
hola, cuanto te tira el error, pone aceptar y despues apreta "ctrl + alt + F1" sin comillas, ahi te aparece un login (todo en consola).
pones user y pass, y despues pones "sudo nano /etc/X11/xorg.conf", ahi te pide la contraseña again, y vas hasta la seccion screen y le pones driver "nv".
guardas, y salis.
ahi pones "sudo /etc/init.d/gdm restart" y ahi estas reiniciando la parte grafica, supuestamente tiene que andar, y mostrarte todo sin nada de nada, sin aceleracion nada. 
una vez ahi, bajate el envy o instala el driver como vos quieras. salu2!!

---

### Post by Mauro22 on 2007-10-09
> Lo de control alt Fx, no funciona.... es como que la PC se cuelga...

Ayer usando una copia del xorg, pude levantar el kernel nuevo en modo Low Graphics, usando vesa.


Ahora estoy actualizando otra vez, son casi 100mb. por ahi funciona despues de esto.


Gracias, Salu2


Resuelto, levante el modo grafico usando vesa, actualice el sistema, reincie, estaba peor pero levanta el modo grafico. 
Reemplaze el xorg.conf con un backup que tenia. Reinicie y voilá. 

De maravillas!!

---

