---
title: "Youtube"
date: 2008-03-08
forum: Argentina Team
---

### Post by ghertzan on 2008-03-08
:lolflag:
Buenas, Soy muy nuevo en esto y en linux tambien,
instale ubuntu hace un par de horas y cuando ingreso a you tube e intento ver un video funciona un momento y al rato se me tilda el sistema no se mueve ni el mouse, tienen idea que puede ser....

GRACIAS!!!!

---

### Post by Apokalyptica79 on 2008-03-09
Hola ghertzan, podés ser un poco más específico a la hora de plantear tu problema?
Por ejemplo danos más información acerca de la pc donde instalaste ubuntu y que versión es.
Saludos

---

### Post by ghertzan on 2008-03-09
Gracias por contestar, 
instale la version para amd64 7.10.
la maquina es un AMD64X2 +4000 - 2GbRAM - GeForce7300GS - SATA
El sistema Instalo los ultimos controladores de la placa de video, yo creo que es eso, puesto que a veces cuando ejecuto juegos se clava todo el sistema...

---

### Post by niko_3100 on 2008-03-10
Yo creo que es porque instalaste la version de 64 bits, proba instalando la de 32 bits. Total no vas a sentir la diferencia ya que todavia el hardware no soporta para 64 bits los buses y eso son todo de 32 bits, por ahora...

---

### Post by Spyco on 2008-03-11
gente yo ando medio nuevo en este ubuntu, y dado que mi mayor preocupacion es esa misma que se plantea aca paso a explicar,
tengo un amd64 4000+ sobre una mother asus n32 sata 2 400gb 2gb mem dual channel 800mhz video 7300gt, funcionaria mejor el 64 o el 32 para esta config?

---

### Post by ghertzan on 2008-03-11
:confused:niko3100
Quise instalar la version de 32bits, bootea todo lindo hasta cuando pongo para iniciar el liveCD y me da este error 
[    0.48000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.48000] Kernel panic - not syncing: IO-APIC + timer doesn't work!
Boot with apic=debug and try booting, whit the 'noapic' option

CHAN!!!!!!!!!!!!
No entiendo nada... y como no conozco mucho de linux es como mandarin para mi....
Tendras idea que puede pasar, el cd de instalacion es uno que pedi.

---

### Post by facundocorradini on 2008-03-11
> gente yo ando medio nuevo en este ubuntu, y dado que mi mayor preocupacion es esa misma que se plantea aca paso a explicar,
tengo un amd64 4000+ sobre una mother asus n32 sata 2 400gb 2gb mem dual channel 800mhz video 7300gt, funcionaria mejor el 64 o el 32 para esta config?

Les recomiendo a todos los que recién empiezan que instalen la versión de 32 bits, aún en sistemas de 64. Van a tener muchos menos dolores de cabeza...

-------------------------------------------------
> Quise instalar la version de 32bits, bootea todo lindo hasta cuando pongo para iniciar el liveCD y me da este error
[ 0.48000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 0.48000] Kernel panic - not syncing: IO-APIC + timer doesn't work!
Boot with apic=debug and try booting, whit the 'noapic' option

CHAN!!!!!!!!!!!!
No entiendo nada... y como no conozco mucho de linux es como mandarin para mi....
Tendras idea que puede pasar, el cd de instalacion es uno que pedi.

Ajá, es Mandarín Avanzado para todos nosotros, pero traduciendo la parte en ingles de lo que te dice, booteá con la opción "noapic"

En el menú de booteo, elegí "other options" (no me acuerdo si se elige o hay que tocar alguna tecla Fn), escribí noapic, dale entre y bootea.

---

### Post by dondionisio on 2008-03-11
Vea, m' hijo, yo he tenido el mesmo problema, y lo he solucionao muy fácil. Vaya a **Aplicaciones -> Accesorios -> Termina**l, y en la consola escriba:
**sudo apt-get install flashplugin-nonfree**
Esa orden le va a correr un escript brasilero que le intala el Flash Player 9 de 32 bit y lo hace funcionar en un sistema de 64 bit. Eso es todo, endespué cuando entre a Yutúb o cualquier sitio con animaciones flash las va a poder ver sin problema.
Si quiere más detaye, visite [http://www.psicofxp.com/forums/gnu-linux.50/562126-howto-flash-player-9-kubuntu-ubuntu.html]("http://www.psicofxp.com/forums/gnu-linux.50/562126-howto-flash-player-9-kubuntu-ubuntu.html")
(ahí está la descrición de la descubridora del escript)

Ojalá le sirva el dato.

Dionisio Rearte
Desperto Informático Crioyo

---

### Post by faktorqm on 2008-03-12
para todos no! 

anda a un terminal y escribi 

```
sudo gedit /boot/grub/menu.lst
```

y busca donde aparezca algo parecido a esto:

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eb24663d-f716-46a5-9c73-36af60219625 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

ahi en la linea que dice kernel le agregas a la derecha de "splash" apic=noapic

te tiene que quedar asi:

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eb24663d-f716-46a5-9c73-36af60219625 ro quiet splash apic=noapic
```

y ahi reinicias y te fijas que te dice, si te sigue diciendo lo mismo le das con nolapic y fijate en la bios tambien que tenes, si tenes apm o apic. es un detalle importante ese, si activas acpi y tenias apm capaz se te soluciona el problema sin tocar nada. Salu2!

---

### Post by ghertzan on 2008-03-22
Hola Gente!
Aca estoy, probe todo lo que me dijeron y no puedo.
Estoy de vuelta con el Innombrable, por que al ultimo se me clavaba todo cualquier cosa que hacia. Ojo, que sigo buscando el inet no me doy por vencido tan facil!

Saludos y Muchas gracias por su ayuda!!!

---

