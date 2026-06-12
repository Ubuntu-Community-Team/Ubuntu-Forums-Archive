---
title: "xubuntu no se apaga"
date: 2007-08-29
forum: Argentina Team
---

### Post by javier-2714 on 2007-08-29
hola a todos  instale xubuntu 7.04 va perfecto pero no apaga estuve goggleando y e probado con agregar al /etc/modules acpi=off apm=power_off y nada despues el boot  cpi=off apm=power_off y no me arranco mas lo tuve que sacar tambien actualice el bios y no hay forma alguna idea agradeseria toda ayuda .

pc mother pc chip m810 ram 256 dico 60 gb .

---

### Post by faktorqm on 2007-08-29
hola vieja!! yo tengo la misma mother y tampoco apaga solo. es un garron. voy a probar tus tips (me los podrias explicar mejor?, gracias de antemano) y si encuentro la solución te aviso. Con win98 tampoco me apaga, habia que ponerle el famoso parche de apagado para que lo haga.
El mensaje en el inicio de algo del 1997 y el 2000 te lo muestra? salu2!!

---

### Post by javier-2714 on 2007-08-30
Mira lo que yo encontre en otros foros es asi;
 
 sudo nano /etc/modules 
y agregas esto :  acpi=off apm=power_off

sudo nano /boot/grub/menu.lst
y agregas esto;   cpi=off apm=power_off
al final de tu opcion que ingresas a xubuntu

quedaria asi:
/boot/vmlinuz-2.6.20-16-generic root=UUID=8dbf7c06-3779-4d83-b2b6-52e8c990139c ro quiet splash locale=es_ES cpi=off apm=power_off

tambien dicen que tenes que actualizar el bios pero nada de todo esto me sirvio probalo suerte.

---

### Post by faktorqm on 2007-08-31
```
quedaria asi:
/boot/vmlinuz-2.6.20-16-generic root=UUID=8dbf7c06-3779-4d83-b2b6-52e8c990139c ro quiet splash locale=es_ES cpi=off apm=power_off
```

hola. esto esta mal, por eso no te anda. por asociacion directa con lo que me escribiste arriba, donde dice "cpi=off" debe ir "acpi=off".

```
sudo nano /boot/grub/menu.lst
y agregas esto; cpi=off apm=power_off
al final de tu opcion que ingresas a xubuntu
```

aca lo mismo. aparte de todo, por lo que veo estas configurando el linux para usar apm en lugar de acpi, asi que anda hasta el bios y la opcion que te aparece como APM/ACPI (en la seccion power management) dejala como APM solo.
Yo hoy cuando llego a casa lo pruebo y te digo. Gracias y salu2!!!!!!!!!!!!

p.d.: la ortografia please!!!!!!! :D:D

---

### Post by javier-2714 on 2007-08-31
Capo probe arreglando y poniendo " acpi=off apm=power_off" y el bios lo puse en  apm pero  nada no quire apagar   me pone pantalla negra (456.913103) system halted
tengo que tener presionado el boton apagar  para que apague una duda en el  sudo nano /etc/modules  esta bien asi ;
 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

# acpi=off apm=power_off

fuse
lp

si encontras otro error avisame o alguna otra forma saludos.

---

### Post by faktorqm on 2007-09-02
Capo, esta mal eso también.

Lines beginning with "#" are ignored.

# acpi=off apm=power_off

Las líneas que comienzan con "#" (numeral) son ignoradas dice ahí. y tu línea aparece con numeral, asi que se lo tenés que sacar.

Yo probé poner el BIOS en apm y hacer lo que me dijiste, y ya por lo menos no me tira el error del inicio del acpi. No apaga, pero por lo menos no tira error. 
Yo no hice nunca update de bios, y si lo hice la verdad no me acuerdo. voy a intentar lo del etc/modules, despues actualizando el bios, y te cuento que paso, si sigue igual, sigo investigando por otra parte a ver como solucionarlo. seguro hay solucion, es cuestion de ponerse. salu2!

---

### Post by javier-2714 on 2007-09-02
Capo ya esta encontre lo que estaba mal apaga en un segundo  lo pongo todo bien como tiene que ser al final.

---

### Post by faktorqm on 2007-09-02
grosssoooo, eso era exactamente lo que encontre en un foro que decia que funcionaba de 10, pero sin editar el menu.lst. 
yo lo voy a probar sin hacer lo del menu.lst a ver si anda, capaz hay que tocar eso solo y el resto esta de más, aunque pensandolo friamente capaz ahi tambien por que resuelve el error que te tira del apic failoff en el inicio, lo pruebo, espero que ande y me alegra que hayas resuelto el problema, y que hayas posteado la solucion. 

Hay un igual de mas en el modules, disculpa que sea rompe, pero si viene alguien que no entiende mucho, copia y pega, y no le va a funcionar. abrazo y desde ya muchas gracias!!

---

### Post by faktorqm on 2007-09-03
Funcionó perfectamente, sin hacer update de BIOS. no pude llegar a probar de sacar lo del menu.lst. salu2!!

---

### Post by javier-2714 on 2007-09-03
Capo ya esta encontre lo que estaba mal apaga en un segundo  lo pongo todo bien como tiene que ser:

sudo nano /boot/grub/menu.lst
y agregas esto; acpi=off apm=power_off
al final de tu opcion que ingresas a xubuntu o ubuntu, en caso de ser ubuntu usar "gedit" en lugar de nano.

quedaria asi:
/boot/vmlinuz-2.6.20-16-generic root=UUID=8dbf7c06-3779-4d83-b2b6-52e8c990139c ro quiet splash locale=es_ES acpi=off apm=power_off

sudo nano /etc/modules
y agregas esto :  apm power_off=1

quedaria asi;

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
apm power_off=1

bueno espero que te funcione a mi me quedo de 10 suerte saludos.

---

### Post by javier-2714 on 2007-09-03
Lo del  menu.lst  es para corregir el error que te tira cuando inicia en nuestro caso hay que dejarlo depende del mother ,al que no le tire error al iniciar no hace falta que lo ponga solamente agregar en el  /etc/modules .No me rompe para nada es lo que me gusta y por lo que me pase de win a ubuntu la gran comunidad y gran predisposicion de todos para ayudar,yo empese hace poco gracias a vos por corregirme saludos.

---

