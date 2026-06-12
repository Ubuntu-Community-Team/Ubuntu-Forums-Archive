---
title: "noacpi se desactiva:S"
date: 2008-03-28
forum: Argentina Team
---

### Post by xpelaox on 2008-03-28
Hola gente que tal?

Les cuento mi problema, resuta que tengo que Bootear ubuntu con NOACPI por que sino no me reconoce automaticamente los puertos usb, es decir, si cuando estoy usando la notebook conecto un mouse, no lo reconoce, tengo que reiniciar la maquina, tambien me pasa que la touch screen funciona lento.

Cuando pongo Noacpi funciona por un tiempo, pero despues como que el acpi se vuelve a activar y  los problemas vuelven.

Alguien sabe como podria hacer para solucionarlo?

Gracias gente!

---

### Post by euzkoarima on 2008-03-28
No estoy seguro de entenderte bien, pero instale ubuntu en una pc (que no es mia) que ya tenia win, y no puedo deshabilitar acpi en el bios porque sino win no anda, entonces le puse noacpi en el menu.lst del grub (supongo que vos también lo pusiste ahí cuando hablas de bootear con noacpi)

El tema es que cada vez que hay una actualización que toca algo del kernel o relacionado y como consecuencia de la actualización toca el menu.lst del grub, me saca el noacpi y a la siguiente vez no arranca, tengo que desactivar en la bios, entrar, volver a agregar noacpi en el grub, etc, etc

Quizas vos si podes reiniciar pero despues no te funciona el usb.
Lo que no se es si te deja de andar después de una actualización (entoces la pegué) o si arrancas, te anda un rato y sin actualizar y ni volver a arrancar te deja de andar, en ese caso, ni idea :(

Saludos

---

### Post by xpelaox on 2008-03-28
hmmmm yo no edite nada, solo lo agregue desde el boot del grub, decis que tendria que modificar que archivo?

---

### Post by Hei Ku on 2008-03-28
> **euzkoarima said:**
> No estoy seguro de entenderte bien, pero instale ubuntu en una pc (que no es mia) que ya tenia win, y no puedo deshabilitar acpi en el bios porque sino win no anda, entonces le puse noacpi en el menu.lst del grub (supongo que vos también lo pusiste ahí cuando hablas de bootear con noacpi)

El tema es que cada vez que hay una actualización que toca algo del kernel o relacionado y como consecuencia de la actualización toca el menu.lst del grub, me saca el noacpi y a la siguiente vez no arranca, tengo que desactivar en la bios, entrar, volver a agregar noacpi en el grub, etc, etc

Quizas vos si podes reiniciar pero despues no te funciona el usb.
Lo que no se es si te deja de andar después de una actualización (entoces la pegué) o si arrancas, te anda un rato y sin actualizar y ni volver a arrancar te deja de andar, en ese caso, ni idea :(

Saludos

Para que no se borre todo despues de la actualizacion de kernel, despues de modificar el menu.lst tenes que correr

sudo update-grub

---

### Post by euzkoarima on 2008-03-28
Con editar el grub yo me referia al archivo
/boot/grub/menu.lst
(haciendo backup y con cuidado para no romper todo)
buscas la linea de booteo del utuntu y le agregas noapic, por ejemplo en mi menu.lst tengo

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=77cec7e4-db4a-490c-bfbf-23105de56fa7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

cambias la línea que comienza con kernel de modo que quede

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=77cec7e4-db4a-490c-bfbf-23105de56fa7 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


dicho sea de paso, no sabia lo de hacer update-grub, pero ojo, yo no hablaba de actualizar uno el kernel, por ejemplo, compilando. Yo hablaba de updates que te sugiere el synaptic, no me acuerdo justo los nombres de paquetes, pero son los que por ejemplo te dan soporte de idiomas o documentacion o algun update de kernel pero por repositorios. Típico que te manda a reniciar despues del update.

---

### Post by Hei Ku on 2008-03-29
a eso me referia. cuando actualizas el kernel de los repositorios.

si no habias hecho antes update-grub, perdes todos los cambios que habias hecho al menu.lst

---

### Post by xpelaox on 2008-03-29
buenisimo muchachos hize lo que me dijeron, sera cuestion de probar y ver funca todo bien.


Mill graciassss=D


Saludos

---

### Post by euzkoarima on 2008-03-29
> **Hei Ku said:**
> a eso me referia. cuando actualizas el kernel de los repositorios.

si no habias hecho antes update-grub, perdes todos los cambios que habias hecho al menu.lst

OK, pero decime (que no estoy seguro) cual es la secuencia correcta

1) actualizo y antes de reniciar hago el update-grub.
2) primero update-grub y luego actualizo y reinicio.

Supongo que la uno, pero pregunto por las dudas
Ahh, y gracias desde ya, esto me va a ahorrar tiempo en el futuro.

---

### Post by xpelaox on 2008-03-29
a mi si modifico, y despues uso update-grub, me vuelve a la instancia anterior(sin modificar)

es normal?:S

---

### Post by Hei Ku on 2008-03-30
Hay un truco sobre donde modificar, y justamente para eso es el update-grub.
Por lo que me dijeron, deben haber modificado en las lineas que aparecen ya armadas, por ejemplo:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=37c0810f-ab6f-47b8-98de-4b5aa087f558 ro splash noapic nolapic
initrd		/boot/initrd.img-2.6.22-14-generic
```

Si modifican ahi, y corren update-grub, o si actualizan el kernel, van a perder los cambios.

Donde tienen que modificar es al principio, despues de esta linea:

```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
```


Por ejemplo, para agregar noacpi yo lo puse asi:

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash noapic nolapic
```

O sea, las lineas que tienen que cambiar son las comentadas. (las que empiezan con #)

Una vez que las modificaron, corren sudo update-grub

Lo que hace el update-grub (no se si hace algo mas) es armar todas las opciones que estan abajo de acuerdo a lo que ustedes pusieron en las lineas comentadas.

---

### Post by xpelaox on 2008-03-30
acabo de probar lo que dijiste, y parece funcionar, gracias!

Me parece que mi problema sigue igual.... no se es raro, a veces booteo y no me reconoce la placa wifi, y el noacpi como que se desactiva despues de un rato:S

no se que onda:S:S:S:S

---

### Post by Hei Ku on 2008-03-30
te fijaste en los logs a ver si aparece algo?

messages.log es el que te ayude probablemente.

---

### Post by xpelaox on 2008-03-30
Donde estan los logs? no los encuentro:S

esto me esta preocupando la situacion es la siguiente, si el noacpi se desactiva, pero lo mas preocupante que esta pasando, que no se si estara relacionado es esto: apago la notebook. la prendo, bootea todo bien pero simplemente desaparece la placa wifi, puedo rebootear y sigue sin aparecer, ahora bien, si conecto la pc a la red por cable, rebooteo y desconecto el cable de red, magicamente aparece la placa wifi.... :confused:

alguna idea?:S

---

### Post by euzkoarima on 2008-03-31
Primero, los logs estan en /var/log o en forma gráfica Menú Sistemas->Administración->Sucesos del sistema.

Segundo, Gracias Hei Ku, me imprimí lo de como modificar correctamente el grub asi pruebo en la otra pc cuando llegué el momento. De paso les cuento que esa pc solo tiene modem. Lo que hago para actualizarla (por supuesto que no muy seguido) es conectarme con modem, actualizar los repositorios y desconectarme. Despues marco todas las actualizaciones, y genero el script para bajar en otra pc. Con un pendrive bajo esos paquetes en la oficina, y los llevo a la otra pc. Anda de 10.

---

