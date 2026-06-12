---
title: "No me funciona Cool &amp; Quiet en GG"
date: 2008-03-14
forum: Argentina Team
---

### Post by jvto on 2008-03-14
Hola, he estado usando Ubuntu Gusty G hace ya un par de meses y ya lo he reemplazado por Wintendo. Me encanta este SO y funciona todo de maravilla, el unico problema que tengo es la funcion cool & Quiet que aparentemente no esta activada cosa que si en Windows.
Lei que en GG esa opcion se activa automaticamente, pero al ver el monitor de frecuencia de cpu siempre sale en 100% y estuve leyendo que con Cool & Quiet este porcentaje disminuiria. Como puedo hacer para activarlo???? Saludos

Como dato: SO Gusty Gibbon, AMD64 +4800 x2, Asus M2N-MX

---

### Post by niko_3100 on 2008-03-14
estas seguro qeu eso es cool & quiet? Porque me parece que eso de variar la frecuencia es 3dnow  fijate el programita powernowd en synaptics.

---

### Post by sajnox on 2008-03-14
Tal vez me equivoco, pero el cool & quit se habilita desde el bios y no desde el SO, por lo menos en mi caso recuerdo habilitado desde el bios

---

### Post by margori on 2008-03-14
Si el CPU siempre sale al 100% entonces es otro el problema y es grave.

Proba entrar a un terminar y escribir "ps -A" y te fijas cual es el proceso que tiene más tiempo de ejecución.

Si es posible, fijate el numero de proceso y escribís "sudo kill xxxx" siendo xxxx el numero de proceso, y chau problemilla por el momento. Luego, cuando reinicies, fijate si el mismo proceso es el problema.

Proba y contanos.

---

### Post by sajnox on 2008-03-14
Perdon, tiene razon margori. 

Aca tenes dos cosas distintas

1) Cool & Quiet es una opcion del cooler de de los micro amd que te permite regular la velocidad en funcion de la temperatura del micro

2) Que tengas el micro al 100% significa que tenes algun/os proceso/s que se comen la maquina y eso no es normal.

Con que estas midiendo el uso del procesador ??

---

### Post by margori on 2008-03-14
Sajnox, me tendrás que disculpar pero tendré que corregir que es Cool & Quiet para que no quede ninguna duda.

Cool & Quiet es una función de las placas madres, y consiste en regular la frecuencia del reloj del micro en función del trabajo que está haciendo. Si no está siendo utilizado, mantiene el reloj a 1600MHz, se gasta poca energía y el micro se mantiene "frio". En el momento que se requiera más capacidad, aumenta el reloj al máximo posible y se obtiene todo el rendimiento del micro.

---

### Post by niko_3100 on 2008-03-15
Eso tambien trae los micros propiamente dicho, yo tengo un sempron con la tecnologia 3dnow que hace eso, es mas me baja de 1800 a 800 mhz, con lo cual lo temrine desinstalando jjeje. Y si seguro que tenes un procesa (programa) que etsa colgado o que te mata el microprocesador, pero debe ser algo colgado porque con ese micro no existe UN solo proceso que consuma el 100% salvo juegos o emuladores obvio.

---

### Post by jvto on 2008-03-19
> 
Cool & Quiet es una función de las placas madres, y consiste en regular la frecuencia del reloj del micro en función del trabajo que está haciendo. Si no está siendo utilizado, mantiene el reloj a 1600MHz, se gasta poca energía y el micro se mantiene "frio". En el momento que se requiera más capacidad, aumenta el reloj al máximo posible y se obtiene todo el rendimiento del micro.
__________________

Perdon, la demora, es como dice margori, En mi caso mi placa no funciona asi en Ubuntu, y en Wintendo si lo hace ¬¬. Obiamente si en Win lo hace esta mas que dicho que lo ya active en la BIOS....
El escalado de CPU lo mido con el medidor de escalado de frecuencia del panel, el cual siempre me da 2.51
El uso de Cpu en reposo es de 5% en un nucleo porque uso Amarok, pero nada mas. segu lei un articulo, el cual no encuentro, el escalado de frecuencia deberia variar con Cool & Quiet, pero como dije antes, no es mi caso... Gracias por responder, prometo responder mas rapido en caso de alguna pregunta

---

### Post by Hei Ku on 2008-03-19
tenes activado el powernowd o el powernow? uno es un daemon, y el otro es un modulo del kernel. El modulo del kernel es el mas recomendable. El nombre especifico cambia de acuerdo a tu procesador, powernow-k8, powernow-k7, etc.
Te fijaste en los logs de inicio si hay algun problema por el cual no los arranca? A mi me pasaba q no los estaba arrancando bien al principio.

---

### Post by jvto on 2008-03-22
Upa, ahi empezo a entrar la pala. He visto en el log

 /var/log/syslog

la siguiente linea que me parece la causante de esto...

Mar 21 05:36:08 jvto kernel: [   28.008000] powernow-k8: MP systems not supported by PSB BIOS structure

Mi bios no soporta powernow de Linux?? eos sera? raro, nunca lei que una ASUS tuviese ese problema...., me faltara habilitar algo en la bios? porque como dije, en Wintendo no tengo ese problema...
Saludos y gracias

---

### Post by Hei Ku on 2008-03-22
A mi me paso algo similar cuando pase de un Athlon 3000 comun al Athlon 3200 X2. El BIOS de la placa no bancaba bien el multicore, asi que tuve que actualizarlo y recien ahi tomo bien las cosas. Hay varios threads por este tema.
En principio, lo que te recomendaria es que te bajes algun gdesklet, screenlet o similar que tenga para ver el uso de multiples CPUs y te fijes que realmente esten andando los dos. Si el kernel no te reconoce los 2 CPUs, tampoco te funciona el powernow. Eso fue lo q me paso a mi.

---

### Post by jvto on 2008-03-22
De hecho si me esta reconociendo y trabajando los dos nucleos

[IMG]http://img221.imageshack.us/img221/9820/sshot1bz7.png[/IMG]
By [jvto](http://profile.imageshack.us/user/jvto) at 2008-03-22

---

### Post by Hei Ku on 2008-03-22
Ok. Con el mensaje de error encontre un par de bugs reportados y un how-to.

Lo primero para hacer te diría que es actualizar el BIOS. Si eso no anda, podes probar con este how-to.

[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/)

La verdad, bastante feito, pero da puntos extra para tu tarjeta de nerd. :D

---

### Post by jvto on 2008-03-22
Buenisimo material.........

Ahora que recuerdo, para instalar ubuntu tuve que Deshabilitar el ACPI support, ese debe ser el tema....... si yo lo habilito me tira un error de ACPI mientras carga ubuntu......
No recuerdo como era, pero me decia algo de ACPI y kernel panic, trate de hacerlo con noapic como sugirieron en varios topics, pero igual me seguia tirando otros errores.....

---

### Post by Hei Ku on 2008-03-22
Con razon, al estar deshabilitado ACPI creo que esto no funca.
Te podes fijar en /boot/grub/menu.lst cual es la opcion que usa el kernel para iniciar por defecto.

---

### Post by jvto on 2008-03-22
Esto sera?

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b48c0461-8652-462d-b20f-369cf26a0c05 ro

---

### Post by Hei Ku on 2008-03-23
es todo ese pedazo y un poco mas, asi se va a armando la opcion del kernel por defecto.
te paso el mio, para que veas:

## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=37c0810f-ab6f-47b8-98de-4b5aa087f558 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash noapic nolapic


Lo que me di cuenta es que yo tengo noapic y nolapic, y sin embargo me funciona el cool and quiet. que opciones tenes vos?

---

