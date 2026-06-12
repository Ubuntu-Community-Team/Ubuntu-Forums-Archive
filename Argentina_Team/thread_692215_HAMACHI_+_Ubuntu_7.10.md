---
title: "HAMACHI + Ubuntu 7.10"
date: 2008-02-09
forum: Argentina Team
---

### Post by User21 on 2008-02-09
Para los que estén familiarizados con [HAMACHI]("http://es.wikipedia.org/wiki/Hamachi"), no habrá preámbulos. Para los que no, TAMPOCO. 

Como instalarlo y ponerlo a funcionar en Ubuntu 7.10?
Pues aqui va:

Descargate Hamachi para Linux desde su [sitio oficial]("https://secure.logmein.com/products/hamachi/download.asp"). no voy a dar la url directa al archivo ni un wget ya que la misma puede cambiar en cualquier momento. No es necesario tampoco crearse un usuario en el sitio.

Antes que nada, instalamos UPX-UCL
```
sudo aptitude install upx-ucl
```Ahora, descomprime el  paquete descargado del sitio de Hamachi e ingresa a la carpeta desde una terminal.

Asumiendo que tu home se llame AURELIO, y bajaste el archivo en el Escritorio, vamos a hacer los pasos:

```
cd /home/AURELIO/Escritorio/hamachi-0.9.9.9-20-lnx
upx -d hamachi 
sudo make install
sudo hamachi-init

```Con eso, habremos instalado y ejecutado Hamachi.

Ahora, como se inicia, se crea un usuario, se inicia o crea sesión en una red virtual? En una consola:
```
sudo hamachi start
sudo hamachi login
```Para unirte a una red: (la de los usuarios de Ubuntu-ar, en este caso; PWD: 21091982)
```
sudo hamachi join ubuntu-ar
```Para mostrarte ONLINE:
```
sudo hamachi go-online ubuntu-ar
```y para ver quienes estan ONLINE:
```
sudo hamachi list
```Con esto, ya tiene tu red virtual a través de Internet.

Para detener el servicio:
```
sudo hamachi stop
```Para mas ayuda, pueden leer el archivo README que viene con el programa descargado o hamachi man en la terminal.

Alguna otra sugerencia o corregir algo? Adelante!
:)

---

### Post by leo_rockway on 2008-02-09
Ya tengo Hamachi funcionando hace un tiempo y es una muy buena aplicación.

Muchas gracias por el CÓMO.

---

### Post by nemodot on 2008-02-09
lei el concepto de Hamachi de la Wikipedia, pero no me queda claro para que tipo de cosas puede ser muy útil. 

Es decir, quiero que me digan, si son tan amables, cual es el uso que le dan a este programa y por que motivo lo recomiendan.

SAludos!

---

### Post by leo_rockway on 2008-02-09
Hamachi es una LAN virtual, es decir que tenés todos los beneficios de una LAN pero a la distancia.

---

### Post by faktorqm on 2008-02-11
yo lo tenia funcionando en mi instalacion anterior con interfaz grafica, igualito que para windows, no me acuerdo que tramoyas habia hecho.... creo que era algo de ghamachi para no tener ke andar tirando comando todo el tiempo. salu2!!

---

### Post by User21 on 2008-02-11
Asi es: hay muchas GUIs para Hamachi dando vueltas por alli. Una vez instalas el Hamachi de esta forma, puedes instalarle las interfases gráficas que desees, de modo de hacerlo mas "user-friendly". :)

---

