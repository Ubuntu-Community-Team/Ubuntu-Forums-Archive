---
title: "temperatura de mi notebook"
date: 2007-10-16
forum: Argentina Team
---

### Post by marcesneibrun on 2007-10-16
Hola Tengo Una Notebook Olivetti 710-430 Vse, Con Ubuntu 7.04, Le Coloqué El Sensor De Temperatura Y La Temperatura Oscila Entre 55 Y 60 Grados, Quería Saber Si Es Muy Alta Osea Si Calienta, Si Es Asi Como Se Puede Bajar La Temperatura, Y Si Alguien Tiene Una Olivetti Y Le Pasa Lo Mismo?
Desde Ya Muchas Gracias
Marcelo

---

### Post by eldragon on 2007-10-16
hola como va.

no parece muy exesiva la temperatura....
de todos modos, dicen que el kernel de gutsy gibbon viene con tecnologia TICKLESS blah blah, que ayudaria a que no trabaje tanto el cpu mientras no hace nada...te sugiero que hagas el upgrade y documentes la diferencia :)

---

### Post by niko_3100 on 2007-10-16
La temperatura de mi compaq v3415 es de lo minimo 37 grados y lo maximo 50 grados, por ahi es el procesador que de por si trabaja a temperatura mas alta. SI es un celeron es asi.

---

### Post by manzuk on 2007-10-16
Yo tengo una Dell 1505 con Ubuntu Feisty, y al temperatura cuando esta enchufada va entre 40 y 60.
Quizá lo que está pasando es que el CPU no está bajando la frecuencia cuando no lo usas...
No se, tiro la idea, habría que ver.
Apoyo lo que dice elDragon sobre Gutsy. Hacete un upgrade (yo voy a hacerme un fresh-install) porque el nuevo release parece que viene con muchas mejoras en administración de energía (yupi! lo necesitábamos)
Saludos!

---

### Post by santiagoward2000 on 2007-10-16
Yo también tengo ese problemita con mi Celeron, nunca baja de 50ºC y a veces llega a 70ºC. Cuando salga Gusty en unos días voy a probar a ver si ayuda.

---

### Post by Hei Ku on 2007-10-16
Esta es una guia para activar el escalado de frecuencia del CPU. O sea, que si el CPU no esta laburando, baje la frecuencia y consuma menos energía. Supongo que les puede servir.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

Avisen cómo anda, porque en el laburo me gané una notebook y pensaba activarle eso cuando la instale.

---

### Post by niko_3100 on 2007-10-17
Mi sempron tiene esa tecnologia 3dnow o algo asi que la instalo sola cuando instale feisty me fije y ya me vino instalo y con conky tengo los datos y si varia la frecuencia del procesador y su temperatura.

---

### Post by jorgito on 2007-10-22
Hola, 

Yo tambien tengo una Olivetti, ahora con Gusty.
La temperatura esta alredor de 55 - 60 grados.
Modifique un poco el .conkyrc que postearon aca para imprimir una temperatura que encontre en: 
/proc/acpi/thermal_zone/THRM

El tema es que no se si eso es valido como medicion de temperatura! 

Supongo ademas que hay una temperatura sola para las dos CPU. Eso sera cierto?

De todos modos, con el conky se ve el cambio de frecuencia de la CPU, sin necesidad de cambiar nada que deje Gusty al arrancar.

Si alguien quiere darle una mirada al .conkyrc lo posteo.

Saludos!

---

