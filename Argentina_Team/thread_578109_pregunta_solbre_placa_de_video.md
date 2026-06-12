---
title: "pregunta solbre placa de video"
date: 2007-10-16
forum: Argentina Team
---

### Post by steve_ignorant on 2007-10-16
bueno gente tengo una placa de video, bastante vieja, pero... se la banca re bien, una GeForce Ti 4200 de 128...

 mi pregunta es si se banca o no el entorno del beryl o del compiz,  porq recien logre conectarla a internet y no tener los drivers de la placa. si me pueden dar una idea de como puedo instalar los drivers y cuales me recomiendan, se los agradeceria mucho. 

agur!

---

### Post by tzulberti on 2007-10-16
para esa placa creo que la instalacion seria:
sudo apt-get install nvidia-glx-legacy

Sino podes ir a System, Administration, algo de drivers (no estoy en ubuntu ahora, estoy con debian). Ahi te deberia de aparecer una opcion para usar el driver de nvidia de tu placa de video.

---

### Post by steve_ignorant on 2007-10-16
mmm hice un sudo apt-get nvidia

o una cosa asi... ahora voy a ver... que onda. y si lo logro hacer andar bien(solo no puedo hacer andar con los efectos de las ventanas) pero al menos la resolucion en 1024 la toma a la parfeccion...

---

### Post by santiagoward2000 on 2007-10-16
> **steve_ignorant said:**
> bueno gente tengo una placa de video, bastante vieja, pero... se la banca re bien, una GeForce Ti 4200 de 128...

 mi pregunta es si se banca o no el entorno del beryl o del compiz,  porq recien logre conectarla a internet y no tener los drivers de la placa. si me pueden dar una idea de como puedo instalar los drivers y cuales me recomiendan, se los agradeceria mucho. 

agur!

Hola steve,
Supongo que se la debe bancar. Ahora estoy usando una ATI Radeon Xpress 200m (es de mi laptop, no se de cuanto sea), y Compiz-Fusion anda bastante bien. Además lo probé en mi PC, que tiene una NVidia GeForce 4400MX de 128 y anduvo bárbaro.
Si estás usando Feisty, yo te recomendaría que uses los drivers que te instala Ubuntu usando el "Restricted Drivers Manager". A mí por lo menos nunca me trajeron ningún problema y es mucho más fácil de instalar.

---

### Post by steve_ignorant on 2007-10-17
mira recien lo hice, eso que me dijiste... y me en el grub me aparece un kernel de 386, y otro de low latency, no se que indica cada uno, pero puse el "normal" osea el que no tiene nada y me tiro error como que no  hay controlador para la placa, 
ahora si elijo el de low latency me corre todo perfecto hasta con el beryl... no se si saben que puede ser?

---

### Post by santiagoward2000 on 2007-10-17
Que raro eso! La verdad que no se que es eso...

---

### Post by steve_ignorant on 2007-10-17
se que tiene que ver con un kernel.... porq en el paquete de actulizaciones vi uno que decia low-latency... pero me llama la atencion, tanto como avos... porq si lo pongo el kernel 2.6.20.16 (o como sean los numeros) generic solo tira error... 

ahora si pongo el mismo pero en low latency entra lo mas comodo. 
tambien no se si lo dije mas arriba, me aparece uno con una opcion kernel(..........) generic 386(?) tampoco se que es eso... 

posiblemente y lo mas seguro es que haya bajado alguna configuracion de kernel por accidente y se esten tirando cachetazos entre uno y otro... porq otro no se me ocurre

---

