---
title: "Se me murio el sonido"
date: 2006-12-11
forum: Argentina Team
---

### Post by quaid on 2006-12-11
Buenas soy nuevo en el foro

A ver quien me peude dar una mano. 

Me paso lo siguiente: 
Tengo Edgy+beryl.
Andaba todo barbaro hasta q:
hace cosa de 1 mes mas o menos no se xq me cambio la ditribucion del teclado, mejor dicho esta en español pero sin la @. En gdm pasa esto, xq por consola andaba barbaro.

No se de donde ni como se me ocurrio cambiar xkb por kbd en xorg.conf. Obviamente pantalla , problema con el servidor X.
Agarro mc edito xorg.conf y listo eso esta solucionado.

Cuando inicio no tenia sonido. Completamente muerto. Probe de todo y n oquiere andar.

**ALguna manera de autodetectarlo? algun comando por consola para configurarlo?** Xq en preferencias->sonido me figura la nvidia ck804, pongo prueba y teoricamente la hace , el tema q no se escucha.

A ver quien me puede dar una mano con eso. gracias.

Al margen:existe algun lugar donde pueda ver una lista de comandos para configurar teclado y etc por consola. Porque todos lados donde busque siempre te dicen como hacerlo con entorno grafico.

Gracias

---

### Post by tzulberti on 2006-12-11
> **quaid said:**
> 

Al margen:existe algun lugar donde pueda ver una lista de comandos para configurar teclado y etc por consola. Porque todos lados donde busque siempre te dicen como hacerlo con entorno grafico.

Gracias

Lo unico que se es que sacaron el comando alasconf para poder volver a configurar la placa de sonido. Ese es el comando que yo usaba en debian. Fuera de eso, del resto no tengo ni idea.

---

### Post by jpmorelli on 2006-12-11
> **quaid said:**
> 

Al margen:existe algun lugar donde pueda ver una lista de comandos para configurar teclado y etc por consola. Porque todos lados donde busque siempre te dicen como hacerlo con entorno grafico.

Gracias

Tenès que tener instalado el paquete console-data y despues podès seguir este tutorial.
[http://www.realidadfutura.com/docu/debian/Castellanizar.html]("http://www.realidadfutura.com/docu/debian/Castellanizar.html")

Lo otro. no se que onda. Supongo que el comando alsaconf puede ayudarte, para eso instala el paquete alsautils y corre alsaconf
Suerte.

---

### Post by felipelerena on 2006-12-11
```
alsa-mixer
``` y subi todo

---

### Post by Nemesis Teufel on 2006-12-12
Vayamos por lo básico..
Solo en ubuntu te pasa? Probaste al menos con el livecd? quizá sea un problema de hard o de tu equipo/parlantes..
No es la primera vez que pasa algo asi.

---

### Post by BlackHero on 2006-12-12
hahhahaha que chistosito xD disculpa que me ria pero me parece chitoso el titulo xD se le murio el sonido xDDDD

---

### Post by quaid on 2006-12-12
Claro, en el live cd no me pasa , en Windows tampoco. El sonido anda perfecto. 
Probe en instlar los drivers de la pagina de realtek para linux y fue peor ahora directamente no reconoce la placa de video.

Otra cosa: alsa-util no trae mas alsaconf, instale casi todos los paquetes de alsa y no esta esa utilidad.

Si no tengo alsaconf , existe manera forma de autodetectar la placa de sonido y q se configure? como lo hago

---

### Post by Nemesis Teufel on 2006-12-12
No se si puede detectar nuevamente.
Quizá una solución sea, reinstalar edgy sin formatear, pero bueno, no creo que sea lo optimo.

---

### Post by ivansv on 2006-12-13
instala edgy sin acpi-acpi=off-al arranque de la instalacion.f6 te lo permite.mi laptop siempre tiene problemas con el sonido si instalo con acpi=on.

---

### Post by quaid on 2006-12-13
Encontre el problema (= media solucion)

La cosa es q estube porbando con el hwinfo --sound
Y me dio lo siguiente:


> quaid@Avion:/home/quaid# hwinfo --sound
15: PCI 04.0: 0401 Multimedia audio controller                  
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_10de_59
  Unique ID: 8otl.gwFUdVJGIiF
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: sound
  Model: "Micro-Star International CK804 AC'97 Audio Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0059 "CK804 AC'97 Audio Controller"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7585 
  Revision: 0xa2
  I/O Ports: 0xf000-0xf0ff (rw)
  I/O Ports: 0xec00-0xecff (rw)
  Memory Range: 0xfe02d000-0xfe02dfff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v000010DEd00000059sv00001462sd00007585bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is not active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Driver Info #1:
    Driver Status: i810_audio is not active
    Driver Activation Cmd: "modprobe i810_audio"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

quaid@Avion:/home/quaid# modprobe snd_intel8x0
WARNING: Could not open '/lib/modules/2.6.17-10-386/kernel/sound/pci/ac97/snd-ac97-bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-386/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.17-10-386/kernel/sound/pci/snd-intel8x0.ko': No such file or directory

quaid@Avion:/home/quaid# 


Bueno agarre me fije en los modulos del kernel y no tenia nada de sonido!
Asi q deduzco q tengo q instalar eso la carpeta "/lib/modules/2.6.17-10-386/kernel/sound/pci" esta vacia.

Como se instala esto?

---

### Post by MeduZa on 2006-12-20
el otro dia hubo un update q toco algo del kernel, me quede sin sonido asi que complile de nuevo los alsa
proba eso
fue mas o menos para la fecha q postiaste esto (recien lo leo)

---

