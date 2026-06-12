---
title: "Mi Primera vez - Consulta"
date: 2008-03-13
forum: Argentina Team
---

### Post by Etrigan on 2008-03-13
Buenas, este es mi primer post y mi primer consulta... Como tambien es la primera vez que puedo disponer de una Pc para instalarle el Ubuntu. 

Acavo de comprar una Dell Vostro 1400 con un Core 2 Duo con bastantes chiches, y quiero corren Ubuntu en ella. 
Segun tengo entendido debo descargar la ultima version de aca [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/) 

Pero me gustaria saber si alguno de ustedes ya a instalado una de estas pc's. para mas o menos saber a que atenerme. 
Segun estube investigando voy a tener problemas con los chips de sonido integrados, son intel. 

Muchas Gracias,

---

### Post by RSLxH on 2008-03-13
Hola Etrigan,

Si que funciona. Hize una busqueda con mi mejor amigo "Google" ;) y encontré esto:
[http://www.linux-on-laptops.com/hosted/Dell-Vostro-1400-Ubuntu-Gutsy.html](http://www.linux-on-laptops.com/hosted/Dell-Vostro-1400-Ubuntu-Gutsy.html)

---

### Post by Mister X on 2008-03-13
yo tengo desde hace unos pocos dias una Vostro 1400, instalé ayer Ubuntu y lo unico que no me funciona es el sonido, aunque no he tenido tiempo de tratar de resolverlo todavia.
lo que te puedo decir si tenes la tarjeta de video intel x3100 y no te anda compiz, lo que tenes que hacer es sacar la placa de la lista negra de compiz, que está en el archivo:

/usr/bin/compiz

---

### Post by Etrigan on 2008-03-13
Lo estube mirando y me dio una muy buena perspectiva , pero habla de "Updating the BIOS", sera eso realmente necesario? 
y la pc que intalaron tiene una NVIDIA - la mia no

---

### Post by Etrigan on 2008-03-13
Excelente, tengo que descargarlo aun (ardua tarea) pero voy a probar y les cuento que tal

---

### Post by leo_rockway on 2008-03-13
Según donde vivas, si lo necesitas quizás alguien te pueda acercar un live cd.

---

### Post by Etrigan on 2008-03-13
Vivo en wilde, y laburo en Barracas, pero ando mucho por el centro y constitucion......
El que estoy descargando es el mismo live Cd, no?

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)
el desktopCD para Intel x86

---

### Post by valucha on 2008-03-13
[COLOR="DarkOrchid"]Yo tuve problemas de sonido con chips intels high definition en 2 notebooks y se solucionaron agregandole unas lineas en un archivo de configuración.
No te preocupes, hay tanta gente con esas placas y ese problema que tutoriales y soluciones sobran.[/COLOR]

---

### Post by sajnox on 2008-03-13
Un gran conocedor de Linux y miembro de la lista de Ubuntu-ar nos ha dejado este link sobre como configuro su dell vostro 1500, si bien no es el mismo equipo estoy seguro que en algo te va a ayudar

[http://tecnicoslinux.com.ar/web/node/218](http://tecnicoslinux.com.ar/web/node/218)

---

### Post by WanderingKnight on 2008-03-14
Si tenés algún drama con lo del Live CD, yo vivo por Barracas, así que de última te puedo alcanzar uno. Avisame cualquier cosa.

---

### Post by Etrigan on 2008-03-17
Ya tengo instalado Ubuntu en mi vostro, 
Consulta........ 
1) me esta solicitando la descarga de 250 MB de actualizaciones, es necesario? esta bajando actualizaciones de las aplicaciones que venian con el CD? El administrador de actualizaciones no tiene un boton " Select All" "Unselect all" 

2) Sonido , no tengo pero estoy investigando cuando tenga dudas mas concretas pregunto. 

3) En el menu apariencia me da la opcion de efectos visuales, pero no me deja activarlos, porque sera esto? 

4)existe alguna forma de agregarle al navegador de archivos una barra de direcciones donde me indique la ruta que estoy explrando? 

Gracias!!!!

---

### Post by faktorqm on 2008-03-17
> **Etrigan said:**
> Ya tengo instalado Ubuntu en mi vostro, 
Consulta........ 
1) me esta solicitando la descarga de 250 MB de actualizaciones, es necesario? esta bajando actualizaciones de las aplicaciones que venian con el CD? El administrador de actualizaciones no tiene un boton " Select All" "Unselect all" 

2) Sonido , no tengo pero estoy investigando cuando tenga dudas mas concretas pregunto. 

3) En el menu apariencia me da la opcion de efectos visuales, pero no me deja activarlos, porque sera esto? 

4)existe alguna forma de agregarle al navegador de archivos una barra de direcciones donde me indique la ruta que estoy explrando? 

Gracias!!!!

1) Bajalas por que son actualizaciones de seguridad y si bien no son "100% vitales", es muy conveniente bajarlas.

2) MARCA Y MODELO DEL CHIPSET DEL AUDIO.

3) Tenes los drivers de la placa de video instalados? 

4) si usas ubuntu, abris el nautilus, apretas IR A y despues a LUGAR y te muestra la ruta en la que estas.

Salu2!

---

### Post by Etrigan on 2008-03-18
Muchisimas gracias, mi sonido ya esta funcionando a la perfeccion.. ahora mi problemas son la placa wireless y el comtrolador de pantalla, mirando un poco encontre esto(que quiere decir?) 
eugenio@eugenio-laptop:/usr/bin$ info

eugenio@eugenio-laptop:/usr/bin$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 


gracias!!

---

### Post by faktorqm on 2008-03-18
fijate el script envy que anda re bien. salu2!

---

### Post by Etrigan on 2008-03-18
No entiendo bien de que trata Envi.. pasame algo mas de data

---

### Post by leo_rockway on 2008-03-18
> **Etrigan said:**
> No entiendo bien de que trata Envi.. pasame algo mas de data

Extraido de la entrada "google" en la wikipedia [0] en español : "Google es, posiblemente, el motor de búsqueda en Internet más grande y más usado."

Y Google[1] es tu amigo si sabes buscar [2]

Y como Google es también mi amigo me tiró esta página [3] (de hecho, fue la primera que apareció).


Salu2
Leo

[0] [http://es.wikipedia.org/wiki/Google#Buscador](http://es.wikipedia.org/wiki/Google#Buscador)
[1] [www.google.com](www.google.com)
[2] [http://www.google.com.ar/search?q=envy+linux+ati+nvidia&ie=UTF-8&oe=UTF-8](http://www.google.com.ar/search?q=envy+linux+ati+nvidia&ie=UTF-8&oe=UTF-8)
[3] [http://www.entrebits.cl/linux/softlinux/envy-para-instalar-en-linux-controladores-de-nvidia-y-ati.html](http://www.entrebits.cl/linux/softlinux/envy-para-instalar-en-linux-controladores-de-nvidia-y-ati.html)

---

### Post by Etrigan on 2008-03-18
Jeejejee..... muchisimas gracias!! 
perdon por mi impaciencia!

---

