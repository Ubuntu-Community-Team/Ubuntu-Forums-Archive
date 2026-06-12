---
title: "Problemon con la placa de video!!!!"
date: 2007-09-24
forum: Argentina Team
---

### Post by nachito on 2007-09-24
Hola mi problema es el siguiente...

 Estando en windows, a mi hermano (pequeño) se le clavo la pc, luego al reiniciar noté que  se habian desinstalado los drivers de mi placa NVDIA Gforce4 MX440, como ya habia pasado antes pensé reinstalar los drivers despues...

 Entonces logie en Ubuntu y me puse a jugar al doom3... luego al rato el doom se empezo a ver como en "cuadraditos" y me tiro un error y se  cerro. Me pareció raro y lo corri de vuelta y ahi se me clavo a maquina de vuelta...

 Cuando quiero entrar al ubuntu de nuevo me aparece una pantalla azul y gris con unso símbolos raros a los costados y me dice que no pudo entrar al modo grafico debido a un fallo de la tarjeta grafica,  por lo que solo puedo entrar a ubuntu en modo consola :S

 Quiero saber si es un problema de software o si se me quemo la placa de video q se yo... de ser asi disculpenme porque no tendria nada q ver con ubuntu.... gracias ...

---

### Post by leo_rockway on 2007-09-24
me imagino que si la placa de video estuviera quemada no podrias ver absolutamente nada y la mother te lo haria saber con unos beeps.

---

### Post by facundocorradini on 2007-09-24
pues parece un problema de hard, específicamente del GPU de la placa de video...
Pero probá el siguiente comando a ver si podés entrar al modo gráfico

sudo dpkg-reconfigure xserver-xorg

te van a aparecer unas cuantas preguntas, respondelas con atención pero sin miedo y si es problema de soft con eso se arregla casi seguro... 

si no, espero que aún tengas la garantía....

---

### Post by nachito on 2007-09-24
Mira, acabo de hacer esa reconfiguracion y le puse como drivers dd dice nvidia pero sigue sin andar el modo grafico, lo demas lo deja como estaba ( cuantas preguntas!)...

Un par de cosas mas:
-En win XP reintsale los drivers un monton de veces y se instalan mal o sea me dice q no pueden inciar...
 -Probe tambien el ubuntu live CD y se me cualga cuando inicia gnome, solo me funciona gnome en modo seguro de garficos o algo asi....


Agrego... el win xp me funciona bien solo q sin la placa de video...

---

### Post by vk-cdg on 2007-09-24
Si tenés problemas tanto en Windows como en Ubuntu todo indicaría que es algo de la placa, pero no te lo puedo asegurar.
Yo probaría la placa en otra PC, aunque sea en Win.

---

### Post by nachito on 2007-09-24
bueno un amigo me dijo que ponga el driver vesa, y ahora funciona pero el ubuntu no pasa de 800x600 y no tengo aceleracion 3D , ya que apenas activo los drivers NVIDIA ( en Sistema>Administracion>Controladores restringidos) no funciona...

alguien sabe q controladores de video trae por defecto ubuntu?

---

### Post by faktorqm on 2007-09-25
La verdad que lo que contas es raro raro, y en mis años jamás habia visto nada parecido, me tuviste pensando todo el dia y no se me ocurrio nada
Lo que se me ocurre asi, sin pensar tanto en el guindous, es que hayas instalado las actualizaciones y que como se te actualizo el kernel, perdiste la configuracion del driver (en realidad la configuracion no, es el modulo del kernel creo), en definitiva, tenes que reinstalar los drivers de nvidia.
si los reinstalas, hacelo con el envy, por las dudas, si ya probaste a mano y no anduvo, hacelo con envy, total perdido por perdido....
otra cosa que  se me ocurre es que realmente tengas una falla en la placa de video, ahora bien, eso que te dijeron, del driver vesa, si bien no esta mal para probar, es el modo mas basico de cualquier placa de video. nunca va a tener aceleracion y tampoco va a pasar de 800x600, por que ya el driver es asi.
pero si te anda bien, y no se te cuelga, tonces tenes mal el driver, (dale con el envy)
la parte de que no te anda en guindous, "la dejo a tu criterio" como karina olga (JAJAKAJAKJAKAJKAJKAJA) recomendacion, reinstala todo si podes. sino, asegurate de borrar los drivers, y el driver cache, y el dll cache.
si hiciste de todo, y estas seguro que lo hiciste bien, yo creo que lo mejor seria que desde un terminal tires "dmesg | grep gforce" y postees el resultado a ver que esta pasando ahi. 
Bueno, espero que haya servido de algo. salu2!!!!!

---

### Post by rojojuan on 2007-09-25
En una máquina tengo instalada esa placa y anda bien en Win y Ubuntu con los drivers de nVidia. Para mi es un problema de Hardware. Podés probar con otra placa de nVidia?

---

### Post by nachito on 2007-09-25
gracias por la explicacion faktoqm... ahora de donde bajo ese driver envy q decis? o ya esta para ponerlo?

---

### Post by nachito on 2007-09-25
disculpame a que te referias con que borre el driver cache? a que borre la carpeta con ese nombre?? y el dll cache?? todo esto es en guindous no?

---

### Post by nachito on 2007-09-26
SIIIIIIIIIIIIIIIII!!!!!!!!!!!!!!!!! xDDDD

Ya esta arreglado se me soluciono SOLO!

Hice lo siguiente: formatie TODO y reinstale windows xp, luego instale los drivers pero no andaban (igual q antes), pero despues de un tiempo... prendo la PC y andaban!!!!!!!!

ahora lo unico q me queda es instalar ubuntu jeje =D


PD: (limpié un poco mi placa antes de instalar win,a lo mejor eso ayudo)

---

### Post by FlyerDie on 2007-09-26
tenias que esperar a que calienten las valvulas...era eso... en frio te pistoneaba.

---

