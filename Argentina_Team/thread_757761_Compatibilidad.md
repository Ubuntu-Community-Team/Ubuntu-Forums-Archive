---
title: "Compatibilidad"
date: 2008-04-17
forum: Argentina Team
---

### Post by AzureSky07 on 2008-04-17
Hola a todos, me presento soy azuresky y ayer mismo mehe bajado el liveCD de ubuntu para probarlo en mi maquina y la verdad me agrado bastante, pero tengo consultas sobre el tema de compatibilidad entre programas, archivos y demas. Actualment estoy en la carrera de sistemas y proximamente estaremos programando en C quisiera saber si es posible ( y me imagino que si ) hacerlo en ubuntu.
Tambien lo que note es que hay algunas cosas que habria que agregarle ya que esta algo "pelado" el ubuntu de entrada y por lo que vi necesita coneccion a internet, habra algun lugar donde pueda sacar esas cosas ( como el codec o el reproductor de mp3 ) sin necesidad de tener internet?

Como veran es mi primera vez en el mundo de linux y tengo serias intenciones de quedarme si el panorama es medianamente favorable ^^

saludos AzureSky

---

### Post by guisheca on 2008-04-17
Mirá, es todo un tema eso de la necesidad de conexión a internet, porque al final es facil pero tenes que tener plata para conectarte a internet, si no, no es tan fácil.
En fin, la solución que uso yo (tengo un amigo que usa ubuntu y no tiene internet, pero yo si), es el programa aptoncd.
Cuando se descarga un paquete desde internet, este se instala en el sistema, pero después no se borra (no se borra lo que sería el "instalador"). Lo que hace aptoncd es hacer un cd con todos los "instaladores" que esten guardados en el sistema, y los pone en forma de repositorio, de manera que, agregando dicho cd a los origenes del software, se podrá instalar el programa deseado mediante synaptic o atitude install.
Yo personalmente, ya tengo hecho dicho repositorio, pero pesa como 400mb no se como haría para pasartelo.
En fin, la solución es tener alguien que use ubuntu y tenga internet, y que te pase los paquetes que necesitas.
Un saludo.

---

### Post by Mister X on 2008-04-17
Con respecto a a programacion en C, por supuesto que podés hacerlo, la  mayoria del sistema está hecho en C y tenes disponible los fuentes, compiladores y herramientas.

Otra opcion para instalar paquetes en tu maquina sin coneccion a internet es desde Synaptic, seleccionas los paquetes normalmente como si estuvieras conectado y te vas al menu Archivo -> Generar script de descarga de paquetes
, eso te genera un archivo que llevas a una maquina con coneccion a internet, los descargas y los incorporas en tu maquina desde Synaptic en la opcion de abajo del menu. Lo bueno de esto es que synaptic te resuelve automaticamente las dependencias de los paquetes y no tenes que hacerlo a mano.

---

### Post by AzureSky07 on 2008-04-17
Muchisimas gracias a ambos por las respuestas ^^ por como viene la mano lo mas seguro es que me pase a ubuntu asi que todo esto me vendra de maravilla ^^ y seguramente me van a tener aca rompiendo las ***** ya que toda mi vida fui un windependiente porque no conocia o no tenia conocimientos para manejar cosas mejores, pero eso cambio ^^

Nuevamente Muchas gracias y adelante 

AzureSky

---

### Post by sajnox on 2008-04-17
> **Mister X said:**
> 

Otra opcion para instalar paquetes en tu maquina sin coneccion a internet es desde Synaptic, seleccionas los paquetes normalmente como si estuvieras conectado y te vas al menu Archivo -> Generar script de descarga de paquetes
, eso te genera un archivo que llevas a una maquina con coneccion a internet, los descargas y los incorporas en tu maquina desde Synaptic en la opcion de abajo del menu. Lo bueno de esto es que synaptic te resuelve automaticamente las dependencias de los paquetes y no tenes que hacerlo a mano.

Muy buen aporte!!!! SI bien no es mi problema, estaba pensando en que soluciones habia para esto.

---

