---
title: "[COMO] Grabadora de DVD con Lightscribe"
date: 2008-03-18
forum: Argentina Team
---

### Post by sajnox on 2008-03-18
Hace un tiempito me compre una grabadora de DVD con lightscribe, en un principio me habia propuesto averiguar un poco cuales eran compatibles con linux y esas cosas, pero ya que iba a comprar una Asus DRW-1814BL, y que generalmente el hard de marca no tiene problemas con Linux. La compre y listo.

Llegue a casa, la instale y obviamente me la reconocio sin un minimo de problemas, solo me faltaba conseguir algun programa que imprimiera sobre los discos, no solo que los grabase.

Consulte a mi amigo Google y encontre esto: 

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

Primero instale las librerias que usa el programa desde esta pagina [http://www.lacie.com/support/drivers/driver.htm?id=10095](http://www.lacie.com/support/drivers/driver.htm?id=10095) 

Luego baje este programa [http://www.lacie.com/support/drivers/driver.htm?id=10094@](http://www.lacie.com/support/drivers/driver.htm?id=10094@)

Y Luego agregue un lanzador para poder accederlo desde el menu de aplicaciones. El lanzador lo cree con gksudo ya que para imprimir sobre el cd pide permisos de root, por lo que el comando del lanzador es el siguiente 
gksudo 4L-gui

Ultimo punto: como los paquetes que baje son rpm y por que soy una persona muy comoda los transforme en .deb con alien, para eso ejecute 
```

sudo alien -v lightscribe-1.8.15.1-linux-2.6-intel.rpm
```
```

sudo alien -v 4L-1.0-r6.i586.rpm
```

Y con eso ya tenia los paquetes deb para instalarlos con un simple doble click.

Espero que a alguien le sirva.

---

### Post by niko_3100 on 2008-03-18
Muy bueno lastima que los cd-r lightscribe estan algo caritos jeje

---

### Post by sajnox on 2008-03-18
> **niko_3100 said:**
> Muy bueno lastima que los cd-r lightscribe estan algo caritos jeje

Si, tampoco creas que grabo todo con lightscribe pero el precio era de $ 20 mas y queria el chiche nuevo

---

### Post by faktorqm on 2008-03-19
comentario que no aporta nada: no siempre te reconoce las cosas de marca.... mi sony dru-810 no aparece ni por casualidad :S

comentario que aporta: muy bueno el como, pero esta realmente bueno eso? nunca vi  como imprime una cosa de esas. Podes imprimir lo que vos quieras digamos, o sea, si pones una foto con un agujero en el medio te la pone en el cd o tenes un area determinada para imprimir? Salu2!!

---

### Post by sajnox on 2008-03-19
Podes imprimir lo que quieras en el area del CD/DVD, fotos/texto y queda realmente muy presentable.

---

### Post by h9005 on 2008-03-19
Alguien sabe como imprimir las caratulas de los dvd y CD? Tengo una samsung.

---

### Post by sajnox on 2008-03-19
> **h9005 said:**
> Alguien sabe como imprimir las caratulas de los dvd y CD? Tengo una samsung.

Si tu grabadora tiene lightscribe con los pasos que puse mas arriba te deberia servir.

---

