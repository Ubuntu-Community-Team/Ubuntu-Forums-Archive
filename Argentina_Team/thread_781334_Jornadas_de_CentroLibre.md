---
title: "Jornadas de CentroLibre"
date: 2008-05-04
forum: Argentina Team
---

### Post by tzulberti on 2008-05-04
Hola. Acabo de llegar de las Jornadas de CentroLibre en Tandil, y este es un resumen de la charla de Felipe de Instalacion de ubuntu (fui solo por  el sabado, por lo que no tengo idea de la otra charla).

Existe un mito que indica que a Felipe le tuvieron que avisar por telefono de su charla...

Ahora vamos a la parte quees 100% verdadera. La charla empieza a las 11:15 porque se atraso la charla de Syslab. Cuando va a empezar, se da cuenta que no tenia cd de Hardy con el cual hacer la demostracion porque se lo habia dado a alguien en dia anterior (lease viernes). Por lo tanto, voy a buscar uno al stand de ubuntu, pero solo teniamos Xubuntu, y Kubuntu que habian sobrado de la Flisol. Cuando subo, felipe ya estaba granando un cd, y empezo a explicar las ventajas de Ubuntu sobre Windows. Por alguna razon, la grabadora se queda durante un largo rato cuando le faltaba un 3%. Felipe se da cuenta que esto es porque se estaba usando la bateria de la laptop, la cual no estaba enchufada.

Una vez que termina de grabarse el cd, los de CentroLibre habian dado una PC con Windows para usarla como conejo de indias. Primero pone el cd sobre Windows, para mostrar Wubi, pero el mismo nunca aparece. Por lo tanto, se  decide reiniciar la PC. Aparece la pantalla de inicio del Cd que todos vimos sin ningun problema, y empieza a bootear. Luego de un rato, aparece algo que seria un error/warning bastantes feo que decir que no se podia leer un bloque del dispositivo /dev/sd0 (que es el mismo error que me tira en mi pc, pero tengo disco IDE). Se penso que era algun problema de la PC, por lo que las personas de CentroLibre habian ido a buscar otra PC.

Lipe se decide hacer la demostracion de la instalacion en el Virtual Box de su laptop, pero en la misma aunque cargaba ubuntu por alguna razon, tardaba en cargar el instalador. Mientras tanto, se vuelve a cambiar el cable del proyecto a la PC y se nota que se habia cargado el instalador. Por lo tanto, se decide seguir la instalacion con la Pc. Se sigue con la instalacion, pero al momento de particionar el disco, aparece como disco de la PC un disco SCSI. Se pasa la parte de particionado y se llega al final, hasta la parte en donde el instalador empieza a copiar los archivos. Sim embargo, la instalacion FALLA (no me acuerdo que decia el mensaje). 

Lipe explica como es que termina la instalacion, y se pone a mostrar cosas con su laptop. Muestra Compiz, en donde todos quedan sorprendidos, junto a un par de juegos, y como hacer para instalarlos. En un momento para mostrar que linux es seguro, decide entrar a la carpeta /bin, e intena de borrar el archivo bash. Ahi le agarro la duda, la cual nunca supe si fue cierta, o mejor dicho miedo de que realmente se borre. Intenta de borrar el archivo, y como todos sabemos, el borrado no continua por temas de permisos.

Ocurrio algo bastante divertido con un incidente con la papelera que no viene al punto.

En resumen: la charla merece un 9.5/10 ya que estuvo muy bien dada, aunque hubo problemas. Los de centroLibre filmaron todo, asique despues van a subir los videos a la pagina de ellos.


Fuera de la charla de Lipe, el evento en general estuvo muy bueno. Bien organizado y con gente con muchas pilas y charlas divertidas. Valio la pena haber ido por el sabado, y lo volveria a hacer el año que viene.

---

### Post by Hei Ku on 2008-05-04
Te hicieron transpirar Lipe!! :lolflag:

Recomendacion, nunca vayas a hacer una demo en una maquina que no conozcas. Es ideal para tener problemas inesperados. :D

---

### Post by marianom on 2008-05-05
Es peor que una pelicula de suspenso... transpiré como loco mientras leia. Te mereces un premio Lipe

---

### Post by felipelerena on 2008-05-05
La cosa es asi:
la maquina esa SI la habiamos provado el dia anterior e iba todo bien.
el CD me lo curtieron del stand y una mina que estaba buenisima me pidio 5 minutos antes de la charla el ultimo que quedaba.
y lo de la papelera... lo que pasa en Tandil queda en tandil.

La charla del viernes estuvo muy muy buena, fueron 300 personas y salio todo bien, lastima que la gente hizo pocas preguntas y despues me tuvieron 2 horas haciendome preguntas en la puerta, hubiera estado bueno que me las hagan en voz alta asi se las respondia a todos, el stand de ubuntu-ar muy bueno, regalamos 300 folletos, 200 papelitos con la dir 25 hardys, y alguien me quizo cortir una empanada.
Hubo muchas charlas muy buenas, hubo una de Bea buzaniche sobre el software libre en el estado bastante interesante, se hablo mucho el tema del SIAP.

La gente de tandil nos trato MUY bien y todo salio muy lindo. lo mejor de todo es que habia mucha gente que no era "del palo"

---

### Post by lega on 2008-05-05
A mi también Hardy me reconoció mi disco IDE como SCSI, no le di bola y seguí, salió todo bien, bueno despues se me quemo la mother, pero no creo que tenga que ver con eso :)

---

### Post by anarko on 2008-05-05
Que pesadilla, lo de las fallidas instalaciones jeje, me intriga lo de la papelera, espero que no te haya pasado lo que me paso ami, que por apurado hice una copia del escritorio en el escritorio y se copio recursivamente 700,000 veces despues lo borre y quedo in enternum en la papelera, hasta que me canse y me decidi a perder un rato de mi vida, abri una consola y le di al sudo rm -R /home/blablabla...blabla/Escritorio(TAB) hasta que entro en todos y patapufeten a volar.
Estaria bueno hacer un treath con los problemas de instalacion que cada uno experimento y como los soluciono, por ej. a mi el instalado jamas pregunto sobre el grub ( hice una instalacion de 0 ) y tube que arrancar con el live CD para instalar el grub y arreglarlo, pero eso lo puede hacer alguien con un poco de cancha por ahi un usuario inexperto se ahoga con una cosa asi, lei en muchos foros que les habia pasado esto mismo, tambien en otra PC el escritorio aparecio en 320x200 y tubimos que ponerle a mano la conf. del monitor y los modos en el xorg.conf son cosas que podrian ayudar a los que recien comienzan.

Saludos.

---

### Post by faktorqm on 2008-05-06
En la ultima pantalla de instalación, antes de apretar "instalar" hay un boton que se llama "avanzado..." Ahi tenes para configurar a donde se va a instalar el grub y si queres podes especificar un proxy tambien. A mi me parece que es cuestion que los users se empiecen a meter un poco en el sistema y no se queden con el siguiente, siguiente, siguiente, foro! no te parece?

Con respecto a lo de tandil, ya estas como el tio bill y su demo de windows 95........ jajajajajajajaj 
yo con la papelera tambien tuve un problema una vez, y le di masa con sudo rm -Rf y despues anduvo todo bien. 
Son cosas que pasan, la onda es no desesperarse, y tambien mostrarle a los users que es la pura realidad, en la muestra siempre te muestran todo ok, cuando vas a tu pc no anda nada y tenes ke empezar a configurar.

Felicitaciones a lipe (y a tzulberti tb) por el trabajo "pesado" de lidiar con pc's que no andan para mostrar soft libre a la gente. La proxima, la pc que anda bajo llave :D jajajaj Salu2!

---

