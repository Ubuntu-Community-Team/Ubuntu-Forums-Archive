---
title: "Xubuntu no me detecta placa de video sis 6326 agp"
date: 2008-04-30
forum: Argentina Team
---

### Post by mrchelo2002 on 2008-04-30
Hola que tal. Instale xubuntu en una maquina un poquito vieja, Pentium III 800mhz, tengo una placa agp Sis 6326, pero no hay forma de configurarla. Siempre inicia en video modo seguro a 640 x 480, y no encuentro donde configurar el hardware.
Intente iniciar con el livecd de ubuntu 8.04, el cual tambien me avisa que no puede encontrar la placa de video, paso a configurarla correctamente desde el listado de controladores, especificando el modelo sis 6236 agp, pero después de aceptar, no vuelve a iniciar.
Debo renunciar a ubuntu/xubuntu, ya que no puedo cambiar la placa, o hay alguna solución? Muchas gracias.

Marcelo

---

### Post by faktorqm on 2008-04-30
Hola, probá con el comando 

```
sudo displayconfig-gtk
```

Espero que lo tengas. Salu2!

---

### Post by mrchelo2002 on 2008-04-30
hola, lo he intentado y siguio igual. Despues de iniciar un par de veces me dio hasta 1024x768, pero no figura en la lista, sino que esta como default.
Busque en el ubuntu y en este y no encuentro el detalle de hardware detectado. Donde esta eso?

---

### Post by mrchelo2002 on 2008-05-04
Hola.

Al final deje la resolucion como más le gusta al sistema. Pero instale el Avanq y al intentar iniciar, se reinicia el entorno gráfico.
Al ejecutar desde la consola, sale un mensaje diciendo que avanq (fllite) no puede conectar con el entorno gráfico, no recuerdo si decía x11 o Xconf.

---

### Post by faktorqm on 2008-05-05
Me fijé y en todos lados dice que el driver "sis" soporta tu placa. El problema es el monitor, no la placa. Si tu modelo de monitor no esta en la lista del displayconfig-gtk entonces mete el cd que te vino con el monitor y decile que te lea el .inf, si no tenes tampoco eso busca las frecuencias de actualizacion horizontal y vertical de tu monitor y ponelas a mano. Reinicia y deberias poder.

nota: no se si es solo en mi pc, pero si pongo testear me testea los cambios pero cuando reinicio es como si no hubiera cambiado nada :( y tengo que volver a ahcer todo de vuelta, y sin testear lo cambia. cosas de linux......

Espero que te haya servido. Salu2!

---

### Post by mrchelo2002 on 2008-05-06
Pruebo y te cuento. o Con otro modelo de monitor, ya que el que tengo lo lista. Pero puede ser que el que va no ande y el que no va ande. Ya cuento que hice y si anduvo. Gracias.,
Saludos!

Marcelo

pd: El monitor es un samsung synmaster 550v

---

