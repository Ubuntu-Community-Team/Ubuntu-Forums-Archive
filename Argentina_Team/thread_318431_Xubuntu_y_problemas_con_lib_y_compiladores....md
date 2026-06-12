---
title: "Xubuntu y problemas con lib y compiladores..."
date: 2006-12-14
forum: Argentina Team
---

### Post by x1r0x on 2006-12-14
El problema es el siguiente:

Como soy nuevo en xubuntu 6.10 pero en el mundo linux(pero eso no significa que sepa mucho) quiero hacer andar xgl... cosa que vi como se hace... perooo el problema es el siguiente... tengo el script para hacer andar el modem que da Telefonica a los usuarios de argentina (El modem usb Speedtouch 330 "la rata plateada") y no puedo hacer instalar por que me empieza a tirar errores de que no tengo ciertas librerias o me falta compiladores... que al parece que en esta distro es comun esto tipos de errores... Asi que no tengo inet para poder acutalizar la distro o poder bajarme los  paquetes para solucionar esto tipo de problemas...

Uno de los errores qye me tira es:

```
C compiler: cannot create executables.
```

y el otro es el siguente:

```
C++ preprocessor "/lib/cpp" fails sanity check
```

Desde ya muchas gracias

---

### Post by pump on 2006-12-14
Primero de todo instala el paquete dev-essentials que te instala los paquetes que necesitas para compilar (compilador y eso). Despues anda fijandote cuando vas a compilar que errores de dependencias te saltan y ahi vas viendo de instalar lo que te pide.

---

### Post by x1r0x on 2006-12-14
> **pump said:**
> Primero de todo instala el paquete dev-essentials que te instala los paquetes que necesitas para compilar (compilador y eso). Despues anda fijandote cuando vas a compilar que errores de dependencias te saltan y ahi vas viendo de instalar lo que te pide.

En packages.ubuntu.com no aparece tal paquete que mencionas. Me podes decir donde lo puedo conseguir. Si te confundis con build-essential, mira que ya lo tengo instalado...

---

### Post by tzulberti on 2006-12-14
El paquete es build-essentials

---

### Post by jpmorelli on 2006-12-15
> **tzulberti said:**
> El paquete es build-essentials


sin la "s"  

build-essential

y gracias por el dato para mi tambien.

---

### Post by lavaramano on 2006-12-16
supongo que lo trataste de hacer funcionar con esta guia:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html)

si es asi, es raro que no te funcione.
yo el otro dia lo hice funcionar en un breezy de una.
eso si, no tengo idea de como funciona(si hubo cambios o algo) edgy, ya que decidi parar el carro en dapper :P

---

### Post by x1r0x on 2006-12-17
> **lavaramano said:**
> supongo que lo trataste de hacer funcionar con esta guia:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html)

si es asi, es raro que no te funcione.
yo el otro dia lo hice funcionar en un breezy de una.
eso si, no tengo idea de como funciona(si hubo cambios o algo) edgy, ya que decidi parar el carro en dapper :P

No no... no uso esa guia para instalar el modem... Me bajo el script con el firmware de esta pagina [http://www.steve-parker.org/speedtouchconf/](http://www.steve-parker.org/speedtouchconf/) y de ahi hay una guia facil...

---

### Post by lavaramano on 2006-12-17
te recomiendo esa de linux-usb.org
ni hace falta compilar.

o sea. tenes que bajar al firmware, al br2684ctl y despues extraer unos archivitos del firmware, copiar unas cosas a /lib/firmware.
configurar la cuenta con el pppoeconf y creo que eso era todo.
despues reinicias, y cuando el modem haya sincronizado. pone 'sudo pon dsl-provider'
y listo. estas en la red de redes :KS

---

